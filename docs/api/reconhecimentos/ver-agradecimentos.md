---
sidebar_position: 6
title: Ver agradecimentos
---

# Ver agradecimentos

Utilize esse método para buscar e visualizar os agradecimentos realizados por colaboradores que receberam reconhecimentos.

## Método

**GET**
`api/v2/recognitions/thanks`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

### Query Parameters (Opcionais)

| Parâmetro      | Tipo   | Descrição                                                  |
| -------------- | ------ | ---------------------------------------------------------- |
| start_date     | date   | Data inicial para filtrar agradecimentos (padrão é início do mês atual) |
| end_date       | date   | Data final para filtrar agradecimentos (padrão é fim do mês atual) |
| sender         | string | `email` ou `registration_id` do colaborador que enviou o reconhecimento |
| receiver       | string | `email` ou `registration_id` do colaborador que recebeu o reconhecimento |
| user_group_uuid| string | `uuid` do grupo de usuários para filtrar agradecimentos. Consulte a [lista de grupos](/api/grupos-de-usuarios/ver-grupos) para obter os UUIDs disponíveis |

## Exemplo de Requisição

Para buscar agradecimentos com filtros:

```
GET api/v2/recognitions/thanks?start_date=01-10-2025&end_date=31-10-2025&receiver=joao.silva@empresa.com
```

Para buscar agradecimentos por grupo de usuários:

```
GET api/v2/recognitions/thanks?start_date=01-01-2025&end_date=31-12-2025&user_group_uuid=11111111-2222-3333-4444-555555555555
```

Para buscar todos os agradecimentos:

```
GET api/v2/recognitions/thanks
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-10-01",
        "end_date": "2025-10-31"
    },
    "thanks": [
        {
            "recognition_date": "28/08/2025",
            "sender_name": "EDNELSON SILVA",
            "sender_email": "ednelson.silva@empresa.com",
            "sender_registration_id": "000089",
            "receiver_name": "MARCELO MALAGUETA",
            "receiver_email": "marcelo.malagueta@empresa.com",
            "receiver_registration_id": "001109",
            "message": "Excelente trabalho na apresentação do projeto! Sua organização e clareza foram fundamentais para o sucesso da reunião.",
            "thank_date": "03/10/2025"
        },
        {
            "recognition_date": "29/08/2025",
            "sender_name": "CAMILE PAULA",
            "sender_email": "camile.paula@empresa.com",
            "sender_registration_id": "000233",
            "receiver_name": "PATRICIA SANTOS",
            "receiver_email": "patricia.santos@empresa.com",
            "receiver_registration_id": "000556",
            "message": "Parabéns pela iniciativa em melhorar os processos da equipe. Sua proatividade e visão estratégica fazem toda a diferença.",
            "thank_date": "01/10/2025"
        },
        {
            "recognition_date": "03/09/2025",
            "sender_name": "FELIPE FALCONI",
            "sender_email": "felipe.falconi@empresa.com",
            "sender_registration_id": "000602",
            "receiver_name": "JANA FARIA",
            "receiver_email": "jana.faria@empresa.com",
            "receiver_registration_id": "001303",
            "message": "Obrigado pelo suporte constante e pela paciência ao ensinar os novos membros da equipe. Você é um exemplo de liderança.",
            "thank_date": "03/10/2025"
        },
        {
            "recognition_date": "19/09/2025",
            "sender_name": "GABRIEL HOHL",
            "sender_email": "gabriel.hohl@empresa.com",
            "sender_registration_id": "001141",
            "receiver_name": "AUGUSTO NETO",
            "receiver_email": "augusto.neto@empresa.com",
            "receiver_registration_id": "001217",
            "message": "Sua capacidade de resolver problemas complexos e manter a calma sob pressão é impressionante. Obrigado por sempre estar disponível.",
            "thank_date": "02/10/2025"
        },
        {
            "recognition_date": "25/09/2025",
            "sender_name": "CARLOS MENDES",
            "sender_email": "carlos.mendes@empresa.com",
            "sender_registration_id": "001200",
            "receiver_name": "MARIA COSTA",
            "receiver_email": "maria.costa@empresa.com",
            "receiver_registration_id": "001201",
            "message": "Parabéns pelo excelente trabalho no fechamento do projeto. Sua organização e atenção aos detalhes foram essenciais para o sucesso.",
            "thank_date": "04/10/2025"
        }
    ]
}
```

### Exemplo com filtro de grupo de usuários

```json
{
    "filters": {
        "start_date": "2025-01-01",
        "end_date": "2025-12-31",
        "user_group": {
            "name": "Grupo Fictício API",
            "uuid": "11111111-2222-3333-4444-555555555555"
        }
    },
    "thanks": [
        {
            "recognition_date": "15/03/2025",
            "sender_name": "ANTONIO SILVA",
            "sender_email": "antonio.silva@empresa.com",
            "sender_registration_id": "001200",
            "receiver_name": "BEATRIZ AMORIM",
            "receiver_email": "beatriz.amorim@empresa.com",
            "receiver_registration_id": "001201",
            "message": "Excelente trabalho no projeto de automação. Sua dedicação e conhecimento técnico foram fundamentais para o sucesso da implementação.",
            "thank_date": "16/03/2025"
        },
        {
            "recognition_date": "22/06/2025",
            "sender_name": "ELIANE COSTA",
            "sender_email": "eliane.costa@empresa.com",
            "sender_registration_id": "001203",
            "receiver_name": "FABIO MARTINS",
            "receiver_email": "fabio.martins@empresa.com",
            "receiver_registration_id": "001204",
            "message": "Parabéns pela iniciativa em melhorar os processos da equipe. Sua proatividade e visão estratégica fazem toda a diferença.",
            "thank_date": "23/06/2025"
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

```json
{
  "error": "sender not found"
}
```

Nesse caso, verifique se o email ou registration_id do remetente está correto e existe no sistema.

```json
{
  "error": "receiver not found"
}
```

Nesse caso, verifique se o email ou registration_id do destinatário está correto e existe no sistema.

```json
{
  "error": "user group not found"
}
```

Nesse caso, verifique se o UUID do grupo de usuários está correto e existe no sistema.
