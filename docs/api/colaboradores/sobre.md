---
sidebar_position: 0
title: Sobre
---

# Sobre a API de Colaboradores

A WeCare disponibiliza uma API REST para facilitar a integração entre o seu sistema de Gestão de Pessoas e a Plataforma da WeCare.

## Visão geral da integração

![](/img/integracoes/api/api.png)

- **Sistema de Gestão de Pessoas**: onde estão os dados dos seus colaboradores;
- **Camada de Integração**: responsável por transformar e transmitir os dados;
- **API de Colaboradores** da WeCare: recebe os dados via HTTPS e atualiza a Plataforma Web.

## Autenticação

Todas as chamadas à API devem ser autenticadas com um **Bearer Token**.

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Como começar

1. **Mapeie** os dados dos seus colaboradores no sistema interno.
2. **Implemente uma camada de integração** que formate e envie os dados conforme a estrutura exigida.
3. **Utilize chamadas HTTPS** autenticadas para comunicação com a API.
4. **Valide os resultados** pela Plataforma Web da WeCare.
