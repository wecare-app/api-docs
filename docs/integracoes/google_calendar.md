---
id: google_calendar
title: Google Calendar
description: Como configurar integração de Google Calendar para sincronização de agendas com a WeCare
slug: /integracoes/google_calendar
sidebar_position: 4
---

# Google Calendar

Este guia é destinado a empresas que utilizam **Google Workspace** e desejam permitir que a plataforma **WeCare** acesse e sincronize calendários corporativos via **OAuth 2.0** e **Google Calendar API**.

---

## 1. Visão Geral

A integração permite que a WeCare:

- Leia agendas do usuário
- Sincronize eventos
- Registre e atualize compromissos
- Consulte disponibilidade

A autorização é feita **por usuário**, e a empresa cliente mantém controle sobre permissões e acesso.

---

## 2. Informações necessárias para configuração

A equipe de TI da empresa cliente deverá nos enviar:

- `client_id`
- `client_secret`

Esses valores são obtidos no console do Google Cloud.

---

## 3. Passo a Passo de Configuração no Google Cloud Console

1. **Acessar o console**
   - https://console.cloud.google.com/

2. **Criar um novo projeto**
   - Menu “Projetos” → **Criar Projeto**

3. **Habilitar APIs**
   - Ir em: `APIs e serviços` → `Biblioteca`
   - Habilitar:
     - **Google Calendar API**
     - **People API** (opcional, caso queira puxar dados do perfil)

4. **Criar credenciais OAuth**
   - `APIs e serviços` → `Credenciais`
   - Clicar em **Criar credenciais** → **ID do cliente OAuth**
   - Selecionar: **Aplicativo da Web**

5. **Configurar URIs**
   - **Authorized redirect URI:**
     ```
     https://[subdominio].wecare.app.br/calendar/auth/callback
     ```
   - Substituir `[subdominio]` pelo subdomínio da empresa na WeCare.

6. **Definir escopos (scopes)**

   Em `APIs e serviços` → `OAuth consent screen`:

   **Escopos não sensíveis:**
   - `openid`
   - `profile`
   - `email`

   **Escopos sensíveis relevantes:**
   - `https://www.googleapis.com/auth/calendar.readonly` → leitura
   - `https://www.googleapis.com/auth/calendar.events` → leitura/escrita

7. **Configurar Branding / App Verification**
   - `OAuth consent screen` → “App domain”
     - Adicionar domínio:
       ```
       wecare.app.br
       ```
   - Se necessário, enviar para **verificação**, caso os escopos sensíveis estejam habilitados.

8. **Baixar JSON**
   - Em `Credenciais` → Baixar o JSON do Client OAuth
   - Extrair de dentro dele:
     - `client_id`
     - `client_secret`

9. **Enviar dados para WeCare**
   - Enviar `client_id` e `client_secret` via canal seguro.

---

## 4. Escopos Utilizados pela WeCare

| Finalidade | Escopo |
|---|---|
| Identidade do usuário | `openid`, `email`, `profile` |
| Leitura de agendas | `https://www.googleapis.com/auth/calendar.readonly` |
| Criação/edição de eventos | `https://www.googleapis.com/auth/calendar.events` |

---

## 5. Fluxo de Autorização OAuth 2.0

1. Usuário acessa a WeCare
2. É redirecionado para o Google para consentimento
3. Autoriza os escopos solicitados
4. WeCare recebe o token de acesso e refresh
5. A sincronização é feita via Google Calendar API

---

## 6. Segurança e Governança

- IT da empresa pode revogar acesso via Admin Console
- Não são solicitadas permissões de **AdminDirectory** (não há leitura de usuários do Workspace)

---

## 7. Suporte

Para dúvidas ou envio dos dados:

📧 **ti@sejawecare.com.br**
