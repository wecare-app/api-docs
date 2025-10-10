---
sidebar_position: 2
title: Quem não foi reconhecido
---

# Quem não foi reconhecido

Utilize esse método para buscar colaboradores que não receberam reconhecimentos no período especificado.

## Método

**GET**
`api/v2/recognitions/lists/didnt_receive_recognitions`

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

Para buscar colaboradores que não foram reconhecidos com filtros:

```
GET api/v2/recognitions/lists/didnt_receive_recognitions?start_date=01-10-2025&end_date=31-10-2025
```

Para buscar todos os colaboradores que não foram reconhecidos:

```
GET api/v2/recognitions/lists/didnt_receive_recognitions
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-10-01",
        "end_date": "2025-10-31"
    },
    "didnt_receive_recognitions": [
        {
            "name": "ANTONIO SILVA",
            "email": "antonio.silva@empresa.com",
            "registration_id": "000304",
            "status": "Ativo"
        },
        {
            "name": "MARIA SANTOS",
            "email": "maria.santos@empresa.com",
            "registration_id": "000559",
            "status": "Ativo"
        },
        {
            "name": "CARLOS OLIVEIRA",
            "email": "carlos.oliveira@empresa.com",
            "registration_id": "001153",
            "status": "Ativo"
        },
        {
            "name": "ANA COSTA",
            "email": "ana.costa@empresa.com",
            "registration_id": "001166",
            "status": "Ativo"
        },
        {
            "name": "PEDRO MENDES",
            "email": "pedro.mendes@empresa.com",
            "registration_id": "000890",
            "status": "Ativo"
        },
        {
            "name": "FERNANDA LIMA",
            "email": "fernanda.lima@empresa.com",
            "registration_id": "000002",
            "status": "Ativo"
        },
        {
            "name": "ROBERTO ALMEIDA",
            "email": "roberto.almeida@empresa.com",
            "registration_id": "001413",
            "status": "Ativo"
        },
        {
            "name": "JULIANA RODRIGUES",
            "email": "juliana.rodrigues@empresa.com",
            "registration_id": "000878",
            "status": "Ativo"
        },
        {
            "name": "LUCAS PEREIRA",
            "email": "lucas.pereira@empresa.com",
            "registration_id": "000415",
            "status": "Ativo"
        },
        {
            "name": "CAMILA SOUZA",
            "email": "camila.souza@empresa.com",
            "registration_id": "001219",
            "status": "Pendente"
        },
        {
            "name": "RICARDO BARBOSA",
            "email": "ricardo.barbosa@empresa.com",
            "registration_id": "000601",
            "status": "Ativo"
        },
        {
            "name": "VANESSA MARTINS",
            "email": "vanessa.martins@empresa.com",
            "registration_id": "001670",
            "status": "Ativo"
        },
        {
            "name": "DIEGO SANTOS",
            "email": "diego.santos@empresa.com",
            "registration_id": "001270",
            "status": "Ativo"
        },
        {
            "name": "PATRICIA FERREIRA",
            "email": "patricia.ferreira@empresa.com",
            "registration_id": "001076",
            "status": "Ativo"
        },
        {
            "name": "MARCOS OLIVEIRA",
            "email": "marcos.oliveira@empresa.com",
            "registration_id": "001628",
            "status": "Pendente"
        },
        {
            "name": "BEATRIZ AMORIM",
            "email": "beatriz.amorim@empresa.com",
            "registration_id": "001259",
            "status": "Pendente"
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
