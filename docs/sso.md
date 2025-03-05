---
id: sso
title: Single Sign On (SSO)
description: Configuração do SSO SAML 2.0
slug: /sso
sidebar_position: 4
---

# Configuração de SSO na WeCare

## Visão Geral

A WeCare oferece suporte ao **SSO (Single Sign-On)** por meio do protocolo **SAML 2.0**. Atualmente, possuímos integração com Google e Microsoft. Este guia explica como configurar a autenticação SSO para integrar sua solução de identidade com a nossa plataforma.

---

## Informações que precisamos

Para configurar o SSO, precisamos que sua equipe nos forneça as seguintes informações do seu Identity Provider (IdP):

- **Certificado de autenticação de tokens** (para cálculo do **Fingerprint**)
- **URL do Identity Provider (URL de Logon)**

Esses dados são fundamentais para estabelecer a conexão segura entre sua solução de identidade e a WeCare.

---

## Configuração no seu Identity Provider

No seu IdP, configure as seguintes URLs da WeCare:

- **URL de resposta (Assertion Consumer Service URL):**  
  `https://[SUBDOMINIO].wecare.app.br/users/saml/auth`

- **URL de metadados:**  
  `https://[SUBDOMINIO].wecare.app.br/users/saml/metadata`

Substitua `[SUBDOMINIO]` pelo subdomínio da sua empresa utilizado na plataforma WeCare.

---

## Processo de Login

Após a configuração, os colaboradores poderão acessar a plataforma WeCare da seguinte maneira:

1. Acessar:  
   `https://[SUBDOMINIO].wecare.app.br`
2. Clicar no botão de SSO: **Entrar com Google** ou **Entrar com Microsoft**

O processo de autenticação será redirecionado automaticamente ao seu IdP.

---

## Solução de Problemas

Se um colaborador encontrar um erro ao tentar autenticar via SSO, pode ser devido a:

- **Usuário não cadastrado:** O colaborador ainda não foi adicionado à plataforma WeCare.
- **Usuário bloqueado:** A conta do colaborador está desativada ou bloqueada.

Recomenda-se revisar o status do usuário na plataforma e garantir que ele esteja corretamente configurado no IdP.

---

Caso tenha dúvidas ou precise de suporte, entre em contato com nossa equipe técnica por meio do e-mail: [ti@sejawecare.com.br](mailto:ti@sejawecare.com.br)
