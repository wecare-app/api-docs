---
id: sso
title: Guia de Configuração de SSO (SAML 2.0)
description: Como configurar o SSO com a WeCare usando SAML 2.0
slug: /sso
sidebar_position: 4
---

# Guia de Configuração de SSO (SAML 2.0)

Este guia é destinado para empresas que já possuem um **Identity Provider (IdP)** — como Google Workspace, Microsoft Entra ID (Azure AD), Red Hat SSO, Keycloak, entre outros — e desejam integrá-lo à plataforma **WeCare** utilizando o protocolo **SAML 2.0**.

---

## 1. Visão Geral

O **Single Sign-On (SSO)** permite que seus colaboradores acessem a WeCare utilizando as credenciais corporativas, eliminando a necessidade de login e senha adicionais.

A integração é feita por meio do protocolo **SAML 2.0** e segue o fluxo:

1. O usuário acessa a WeCare.
2. O SP (WeCare) envia uma solicitação de autenticação ao IdP.
3. O IdP autentica o usuário.
4. O IdP envia uma resposta SAML para a WeCare validando a autenticação.

---

## 2. Informações necessárias para configuração

Para configurarmos o SSO na WeCare, sua equipe precisa nos fornecer as seguintes informações do IdP:

- **Entity ID** (identificador do IdP)
- **URL de Single Sign-On (SSO URL / Login URL)**
- **Certificado público (X.509) do IdP**  
  - Utilizado para validar a assinatura das respostas SAML.
- **Binding de SSO** (recomendado: HTTP-Redirect para AuthnRequest e HTTP-POST para Response)
- **Formato do NameID** (recomendado: `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress`)
- **Atributos que serão enviados**:
  - `email` (obrigatório)
  - `first_name` (opcional)
  - `last_name` (opcional)
- Confirmação se o IdP **exige que o AuthnRequest seja assinado**.  
  - Caso sim, utilizaremos o **certificado público do SP**.

> **Se disponível**, também pode ser fornecido o **arquivo de metadata/descriptor** do IdP (`.xml`).  
> Esse arquivo contém todas as informações acima (Entity ID, URLs, certificado, formatos suportados) em um único documento padronizado, facilitando e agilizando a configuração no SP.

---

## 3. Informações que disponibilizamos para configuração no IdP

Ao criar a configuração no seu IdP, utilize os dados abaixo:

- **Entity ID (SP)**  
  `https://[SUBDOMINIO].wecare.app.br`

- **Assertion Consumer Service (ACS URL)**  
  `https://[SUBDOMINIO].wecare.app.br/users/saml/auth`

- **Metadata do SP**  
  `https://[SUBDOMINIO].wecare.app.br/users/saml/metadata`

- **Certificados do SP**  
  - **Homologação:** (enviado pela equipe WeCare)
  - **Produção:** (enviado pela equipe WeCare)

> Substitua `[SUBDOMINIO]` pelo subdomínio da sua empresa na WeCare.

---

## 4. Passo a passo para configuração no IdP (Exemplo Genérico)

1. **Crie uma nova aplicação SAML** no seu IdP.
2. **Defina**:
   - ACS URL: conforme informado acima.
   - Entity ID: conforme informado acima.
3. **Selecione o formato do NameID** como `emailAddress`.
4. **Configure os atributos**:
   - `email` → endereço de e-mail corporativo (obrigatório)
   - `first_name` → nome (opcional)
   - `last_name` → sobrenome (opcional)
5. **Habilite a assinatura do AuthnRequest**, se exigido, e importe o certificado público do SP.
6. **Exporte o certificado público do IdP** e envie para a WeCare.
7. **Confirme o binding**:
   - AuthnRequest: HTTP-Redirect
   - Response: HTTP-POST

---

## 5. Mapeamento de Atributos

| Provedor / IdP              | Atributo no IdP                                           | Atributo esperado pela WeCare |
|-----------------------------|----------------------------------------------------------|--------------------------------|
| **Google Workspace**        | `primary_email`                                          | `email`                        |
|                             | `first_name`                                             | `first_name`                   |
|                             | `last_name`                                              | `last_name`                    |
| **Microsoft Entra ID**      | `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress` | `email`                        |
|                             | `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname`   | `first_name`                   |
|                             | `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname`    | `last_name`                    |
| **Keycloak / Red Hat SSO**  | `email` ou `EMAIL`                                        | `email`                        |
|                             | `firstName`                                              | `first_name`                   |
|                             | `lastName`                                               | `last_name`                    |

> Caso o atributo não esteja disponível no IdP, podemos utilizar o **NameID** como fonte de e-mail.

---

## 6. Processo de Testes

### Homologação
- Configure o IdP com os dados e o certificado de **homologação**.
- Realize um teste de autenticação.
- Verifique se os atributos estão chegando corretamente.

### Produção
- Após a homologação, repita a configuração usando o certificado de **produção**.
- Realize os testes finais com usuários reais.

---

## 7. Processo de Login na WeCare

- O usuário acessa `https://[SUBDOMINIO].wecare.app.br`.
- Se o SSO estiver configurado:
  - Pode clicar no botão **Entrar com SSO**.
  - O texto e o ícone do botão podem ser personalizados (ex.: “Entrar com [Nome da Empresa]”).
  - É possível ocultar os campos de e-mail e senha para forçar o uso do SSO.

---

## 8. Personalizações Possíveis

- Alterar o texto do botão de login SSO.
- Ocultar campos de login tradicional.

---

## 9. Boas Práticas

- Mantenha os certificados sempre atualizados para evitar expiração.
- Garanta que o relógio dos servidores esteja sincronizado (NTP) para evitar erros de tempo.
- Controle o acesso por grupos/perfis no IdP.

---

## 10. Suporte

Para dúvidas técnicas ou envio das informações de configuração, entre em contato com nossa equipe técnica:

📧 **ti@sejawecare.com.br**
