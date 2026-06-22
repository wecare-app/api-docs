---
id: microsoft_outlook
title: Microsoft Outlook
description: Como configurar integração de Outlook via Microsoft Entra para sincronização de agendas com a WeCare
slug: /integracoes/microsoft_outlook
sidebar_position: 5
---

# Microsoft Outlook

Este guia é destinado para empresas que utilizam **Microsoft Entra ID (antigo Azure AD)** e desejam integrar seus calendários do **Outlook/Exchange Online** com a **WeCare**, utilizando **OAuth 2.0** e **Microsoft Graph API**.

---

## 1. Visão Geral

A integração permite que a WeCare:

- Leia agendas do usuário
- Consulte disponibilidade
- Crie/edite eventos (opcional)
- Sincronize compromissos

A permissão é **delegada por usuário**, sem necessidade de permissões de administrador para diretório.

---

## 2. Informações necessárias para configuração

A TI deve nos enviar:

- `client_id` (Application ID)
- `client_secret`
- `tenant_id`

Esses valores são obtidos no Entra ID.

---

## 3. Passo a Passo no Portal Microsoft Entra

1. **Acessar o portal**
   - https://entra.microsoft.com/

2. **Registrar nova aplicação**
   - `Identity` → `Applications` → `App registrations`
   - Clicar em **New registration**
   - Configurar:
     - **Name:** WeCare Calendar
     - **Supported account types:** `Accounts in this organizational directory only (Single tenant)`

3. **Adicionar Redirect URI**
   - Tipo: **Web**
   - URI:
     ```
     https://[subdominio].wecare.app.br/calendar/auth/callback
     ```

4. **Gerar Client Secret**
   - `Certificates & secrets` → **New client secret**
   - Guardar o valor (não é visualizado depois)

5. **Anotar IDs**
   - `Application (client) ID`
   - `Directory (tenant) ID`

6. **Adicionar permissões da API**
   - `API Permissions` → `Add a permission` → `Microsoft Graph` → `Delegated permissions`
   - Adicionar:

     **Identidade (equivalente ao Google openid/email/profile):**
     - `openid`
     - `profile`
     - `email`

     **Calendário:**
     - `Calendars.Read` (leitura)
     - `Calendars.ReadWrite` (leitura+escrita)

7. **Consentimento do Administrador**
   - Ainda em `API Permissions`
   - Clicar em:
     ```
     Grant admin consent for <ORGANIZATION>
     ```

---

## 4. Permissões Utilizadas pela WeCare

| Finalidade | Permissão (Microsoft Graph) |
|---|---|
| Identidade do usuário | `openid`, `profile`, `email` |
| Ler eventos | `Calendars.Read` |
| Criar/editar eventos | `Calendars.ReadWrite` |

---

## 5. Fluxo OAuth 2.0 com Microsoft Graph

1. Usuário acessa a WeCare
2. É redirecionado para o Microsoft Login
3. Após consentimento, retorna com token de acesso
4. Renovação via refresh token
5. Consultas via `https://graph.microsoft.com/v1.0/me/calendar`

---

## 6. Comparativo com o Google

| Item | Google | Microsoft |
|---|---|---|
| API | `Calendar API` | `Microsoft Graph` |
| Read | `calendar.readonly` | `Calendars.Read` |
| Write | `calendar.events` | `Calendars.ReadWrite` |
| Identidade | `openid email profile` | `openid profile email` |
| Admin Consent | opcional | recomendado |
| Tenant | Workspace | Entra/Azure |

---

## 7. Segurança e Governança

- Revogação via `Enterprise Applications`
- Permissões **delegadas**, sem leitura de diretório

---

## 8. Suporte

Para dúvidas ou envio dos dados:

📧 **ti@sejawecare.com.br**

