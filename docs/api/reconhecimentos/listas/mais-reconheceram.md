---
sidebar_position: 3
title: Mais reconheceram
---

# Mais reconheceram

Utilize esse método para buscar os colaboradores que mais enviaram reconhecimentos no período especificado, ordenados por quantidade de reconhecimentos enviados.

## Método

**GET**
`api/v2/recognitions/lists/most_sent_recognitions`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

### Query Parameters (Opcionais)

| Parâmetro      | Tipo   | Descrição                                                  |
| -------------- | ------ | ---------------------------------------------------------- |
| start_date     | date   | Data inicial para filtrar (padrão é início do mês atual) |
| end_date       | date   | Data final para filtrar (padrão é fim do mês atual) |

## Exemplo de Requisição

Para buscar os colaboradores que mais reconheceram com filtros:

```
GET api/v2/recognitions/lists/most_sent_recognitions?start_date=01-10-2025&end_date=31-10-2025
```

Para buscar todos os colaboradores que mais reconheceram:

```
GET api/v2/recognitions/lists/most_sent_recognitions
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-10-01",
        "end_date": "2025-10-31"
    },
    "most_sent_recognitions": [
        {
            "position": 1,
            "name": "NICOLE COSTA",
            "email": "nicole.costa@empresa.com",
            "registration_id": "001118",
            "recognitions_count": 5,
            "points": 200
        },
        {
            "position": 2,
            "name": "GUSTAVO ANDRADE",
            "email": "gustavo.andrade@empresa.com",
            "registration_id": "001645",
            "recognitions_count": 4,
            "points": 200
        },
        {
            "position": 2,
            "name": "ALAN SANTOS",
            "email": "alan.santos@empresa.com",
            "registration_id": "000648",
            "recognitions_count": 4,
            "points": 200
        },
        {
            "position": 2,
            "name": "GIOVANNI CURSINO",
            "email": "giovanni.cursino@empresa.com",
            "registration_id": "000344",
            "recognitions_count": 4,
            "points": 200
        },
        {
            "position": 2,
            "name": "RAQUEL PEREIRA",
            "email": "raquel.pereira@empresa.com",
            "registration_id": "000766",
            "recognitions_count": 4,
            "points": 150
        },
        {
            "position": 2,
            "name": "NILBE ROCHA",
            "email": "nilbe.rocha@empresa.com",
            "registration_id": "001077",
            "recognitions_count": 4,
            "points": 100
        },
        {
            "position": 3,
            "name": "FRANCISCA SILVA",
            "email": "francisca.silva@empresa.com",
            "registration_id": "000342",
            "recognitions_count": 2,
            "points": 75
        },
        {
            "position": 4,
            "name": "THIEGO COBOS",
            "email": "thiego.cobos@empresa.com",
            "registration_id": "001243",
            "recognitions_count": 1,
            "points": 50
        },
        {
            "position": 4,
            "name": "VANESSA CRUZ",
            "email": "vanessa.cruz@empresa.com",
            "registration_id": "001206",
            "recognitions_count": 1,
            "points": 50
        },
        {
            "position": 4,
            "name": "MARCELO SILVA",
            "email": "marcelo.silva@empresa.com",
            "registration_id": "001181",
            "recognitions_count": 1,
            "points": 50
        },
        {
            "position": 4,
            "name": "LETICIA SILVA",
            "email": "leticia.silva@empresa.com",
            "registration_id": "000982",
            "recognitions_count": 1,
            "points": 50
        },
        {
            "position": 4,
            "name": "IVANETE SOUZA",
            "email": "ivanete.souza@empresa.com",
            "registration_id": "000960",
            "recognitions_count": 1,
            "points": 50
        },
        {
            "position": 4,
            "name": "JEAN MENDES",
            "email": "jean.mendes@empresa.com",
            "registration_id": "000898",
            "recognitions_count": 1,
            "points": 50
        },
        {
            "position": 4,
            "name": "ISRAEL OBLACK",
            "email": "israel.oblack@empresa.com",
            "registration_id": "000439",
            "recognitions_count": 1,
            "points": 50
        },
        {
            "position": 4,
            "name": "HISTANILENHES OLIVEIRA",
            "email": "histanilenes.oliveira@empresa.com",
            "registration_id": "000433",
            "recognitions_count": 1,
            "points": 25
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

### 400 - Requisição Inválida

```json
{
  "error": "Data inicial inválida"
}
```

Nesse caso, verifique se a data inicial está no formato correto (DD-MM-YYYY).

```json
{
  "error": "Data final inválida"
}
```

Nesse caso, verifique se a data final está no formato correto (DD-MM-YYYY).

```json
{
  "error": "Data inicial deve ser anterior ou igual à data final"
}
```

Nesse caso, ajuste as datas para que a data inicial seja anterior ou igual à data final.

```json
{
  "error": "O intervalo máximo permitido é de 12 meses"
}
```

Nesse caso, reduza o intervalo entre as datas para no máximo 12 meses.
