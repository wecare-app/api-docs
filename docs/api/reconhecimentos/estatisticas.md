---
sidebar_position: 1
title: Estatísticas
---

# Estatísticas de reconhecimentos

Utilize esse método para obter estatísticas detalhadas sobre os reconhecimentos da empresa no período especificado.

## Método

**GET**
`api/v2/recognitions/stats`

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

Para buscar estatísticas com filtros:

```
GET api/v2/recognitions/stats?start_date=01-10-2025&end_date=31-10-2025
```

Para buscar estatísticas do período padrão:

```
GET api/v2/recognitions/stats
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-10-01",
        "end_date": "2025-10-31"
    },
    "general": {
        "participants_count": 150,
        "senders_count": 45,
        "recognitions_count": 28
    },
    "receiving": {
        "users_being_recognized_percentage": 18.67,
        "average_recognitions_per_user": 1.5
    },
    "sending": {
        "users_recognizing_percentage": 30.0,
        "average_recognitions_per_user": 1.87
    },
    "x-ray": {
        "recognitions_per_virtue": {
            "TRABALHO EM EQUIPE": 12,
            "AÇÃO": 8,
            "INCLUSÃO": 5,
            "CURIOSIDADE": 3
        },
        "recognitions_per_additional_virtue": null,
        "recognitions_per_area": [
            {
                "name": "INCLUSÃO",
                "data": {
                    "SÃO PAULO": 2,
                    "RIO DE JANEIRO": 2,
                    "MINAS GERAIS": 1
                }
            },
            {
                "name": "MAESTRIA",
                "data": {
                    "SÃO PAULO": 3,
                    "RIO DE JANEIRO": 1,
                    "MINAS GERAIS": 1
                }
            },
            {
                "name": "Propósito",
                "data": {
                    "SÃO PAULO": 1,
                    "RIO DE JANEIRO": 1
                }
            },
            {
                "name": "AÇÃO",
                "data": {
                    "SÃO PAULO": 4,
                    "RIO DE JANEIRO": 2,
                    "MINAS GERAIS": 2
                }
            },
            {
                "name": "CURIOSIDADE",
                "data": {
                    "SÃO PAULO": 2,
                    "RIO DE JANEIRO": 1
                }
            },
            {
                "name": "TRABALHO EM EQUIPE",
                "data": {
                    "SÃO PAULO": 6,
                    "RIO DE JANEIRO": 3,
                    "MINAS GERAIS": 3
                }
            }
        ]
    },
    "engagement": {
        "likes_count": 22,
        "average_likes_per_recognition": 0.79,
        "comments_count": 8,
        "average_comments_per_recognition": 0.29,
        "shares_count": 3,
        "average_shares_per_recognition": 0.11
    },
    "points": {
        "distributed_points": 8400,
        "used_points": 1120,
        "used_points_percentage": 13.33,
        "average_points_per_recognition": 40.0
    }
}
```

### Descrição dos Campos

#### **general**
- `participants_count`: Total de participantes no período
- `senders_count`: Total de usuários que enviaram reconhecimentos
- `recognitions_count`: Total de reconhecimentos enviados

#### **receiving**
- `users_being_recognized_percentage`: Percentual de usuários que receberam reconhecimentos
- `average_recognitions_per_user`: Média de reconhecimentos recebidos por usuário

#### **sending**
- `users_recognizing_percentage`: Percentual de usuários que enviaram reconhecimentos
- `average_recognitions_per_user`: Média de reconhecimentos enviados por usuário

#### **x-ray**
- `recognitions_per_virtue`: Contagem de reconhecimentos por valores
- `recognitions_per_additional_virtue`: Valores adicionais (pode ser null)
- `recognitions_per_area`: Array com reconhecimentos por área organizacional

#### **engagement**
- `likes_count`: Total de likes dados aos reconhecimentos
- `average_likes_per_recognition`: Média de likes por reconhecimento
- `comments_count`: Total de comentários nos reconhecimentos
- `average_comments_per_recognition`: Média de comentários por reconhecimento
- `shares_count`: Total de compartilhamentos
- `average_shares_per_recognition`: Média de compartilhamentos por reconhecimento

#### **points**
- `distributed_points`: Total de pontos distribuídos
- `used_points`: Total de pontos utilizados
- `used_points_percentage`: Percentual de pontos utilizados
- `average_points_per_recognition`: Média de pontos por reconhecimento

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
