---
sidebar_position: 2
title: Ver grupo de usuários
---

# Ver grupo de usuários

Utilize esse método para buscar e visualizar um grupo de usuários específico, incluindo a lista de usuários pertencentes ao grupo.

## Método

**GET**
`api/v2/user_groups/{uuid}`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

### Path Parameters

| Parâmetro | Tipo   | Descrição                    |
| --------- | ------ | ---------------------------- |
| uuid      | string | UUID único do grupo de usuários |

## Exemplo de Requisição

```
GET api/v2/user_groups/11111111-2222-3333-4444-555555555555
```

## Resposta

### 200 - Sucesso

```json
{
    "user_group": {
        "name": "Grupo API",
        "users_count": 3,
        "uuid": "99b8caf2-3cb1-48b0-8198-592a25764700"
    },
    "users": [
        {
            "admission_date": "13/06/2022",
            "area": {
                "level_1": "LIMÃO",
                "level_2": "NOVOS NEGOCIOS",
                "level_3": "PATRICIA JUCELINA DOS SANTOS"
            },
            "birth_date": "26/05/1989",
            "cellphone": null,
            "email": "felipe.falconi@empresa.com",
            "function": "GER. PESQ. DESENV.",
            "manager": {
                "name": "PATRICIA JUCELINA DOS SANTOS",
                "email": "patricia.santos@empresa.com",
                "registration_id": "001001"
            },
            "name": "FELIPE MENDES FALCONI",
            "registration_id": "001002",
            "status": "active"
        },
        {
            "admission_date": "04/07/2011",
            "area": {
                "level_1": "MANAUS",
                "level_2": "MONTAGEM",
                "level_3": "LUCIANO BRANCO COSTA"
            },
            "birth_date": "13/02/1981",
            "cellphone": "11999999999",
            "email": "luziete.anjos@empresa.com",
            "function": "AUX. DE MONTAGEM",
            "manager": {
                "name": "PRISCILA SIQUEIRA DA SILVA",
                "email": "priscila.silva@empresa.com",
                "registration_id": "001003"
            },
            "name": "LUZIETE SILVA DOS ANJOS",
            "registration_id": "001004",
            "status": "active"
        },
        {
            "admission_date": "13/11/2024",
            "area": {
                "level_1": "CD",
                "level_2": "TRANSPORTES",
                "level_3": "CARLA CARVALHO WIVAS E GOMES"
            },
            "birth_date": "21/11/1988",
            "cellphone": "11988888888",
            "email": "elisabete.mendes@empresa.com",
            "function": "ASSIST DE TRANSPORTE",
            "manager": {
                "name": "POLLYANA FAGUNDES MASSON",
                "email": "pollyana.masson@empresa.com",
                "registration_id": "001005"
            },
            "name": "ELISABETE MARIA DE ANDRADE MENDES",
            "registration_id": "001006",
            "status": "active"
        }
    ]
}
```

### 401 - Não Autorizado

```json
{
  "error": "access token expired"
}
```

Nesse caso, verifique se o `access_token` no header `Authorization` está correto e não expirou.

### 404 - Grupo não encontrado

```json
{
  "error": "user group not found"
}
```

Nesse caso, verifique se o UUID do grupo está correto e existe no sistema.
