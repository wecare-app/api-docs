---
sidebar_position: 1
title: Ver grupos de usuários
---

# Ver grupos de usuários

Utilize esse método para buscar e visualizar todos os grupos de usuários da empresa.

## Método

**GET**
`api/v2/user_groups`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

Este endpoint não possui parâmetros.

## Exemplo de Requisição

```
GET api/v2/user_groups
```

## Resposta

### 200 - Sucesso

```json
[
    {
        "name": "Grupo API",
        "users_count": 3,
        "uuid": "99b8caf2-3cb1-48b0-8198-592a25764700"
    },
    {
        "name": "Grupo de Desenvolvedores",
        "users_count": 25,
        "uuid": "11111111-2222-3333-4444-555555555555"
    },
    {
        "name": "Grupo de Vendas",
        "users_count": 15,
        "uuid": "22222222-3333-4444-5555-666666666666"
    },
    {
        "name": "Grupo de RH",
        "users_count": 8,
        "uuid": "33333333-4444-5555-6666-777777777777"
    }
]
```

### 401 - Não Autorizado

```json
{
  "error": "access token expired"
}
```

Nesse caso, verifique se o `access_token` no header `Authorization` está correto e não expirou.
