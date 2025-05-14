---
id: email
title: Liberação de Email
description: Liberação do IP dedicado da WeCare para envio de notificações por email
slug: /email
sidebar_position: 5
---

# Liberação de Email

A WeCare utiliza o serviço da SendGrid para o envio de notificações por email aos seus clientes e colaboradores. Para garantir a entrega adequada das mensagens, é importante que nosso endereço IP de envio seja liberado (adicionado à whitelist) nas ferramentas de filtragem de emails dos destinatários.

## Por que liberar o IP?

Alguns servidores de email, firewalls corporativos e gateways de segurança podem colocar mensagens em quarentena ou bloqueá-las caso identifiquem envios vindos de IPs não confiáveis ou desconhecidos. Isso pode comprometer a entrega de notificações importantes da plataforma.

## Informações técnicas

- **IP dedicado:** `149.72.209.23`
- **SMTP:** `http://smtp.sendgrid.net/`
- **Porta:** `587`
- **Segurança:** TLS (StartTLS)
- **Provedor:** Twilio SendGrid

## Segurança e confiabilidade

A WeCare utiliza um IP **dedicado** para envio de emails transacionais, o que significa que o endereço IP não é compartilhado com outros remetentes. Isso reduz significativamente os riscos de reputação e bloqueios indevidos.

O tráfego de email é protegido com criptografia TLS, garantindo que os dados em trânsito não possam ser interceptados ou alterados. Toda a infraestrutura de email é hospedada pela Twilio SendGrid, uma das plataformas mais reconhecidas e confiáveis do mercado para envio de email em larga escala.

## Recomendação

Para assegurar a entrega dos emails da WeCare, recomendamos que o IP `149.72.209.23` seja incluído na whitelist dos servidores e filtros de email utilizados pela sua organização. Também é importante garantir que a porta 587 esteja liberada para comunicação SMTP com TLS.

---

Caso tenha dúvidas ou precise de suporte, entre em contato com nossa equipe técnica por meio do e-mail: [ti@sejawecare.com.br](mailto:ti@sejawecare.com.br)
