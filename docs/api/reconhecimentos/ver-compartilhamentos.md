---
sidebar_position: 6
title: Ver compartilhamentos
---

# Ver compartilhamentos

Utilize esse método para buscar e visualizar os compartilhamentos de reconhecimentos realizados pelos usuários em redes sociais.

## Método

**GET**
`api/v2/recognitions/shares`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

### Query Parameters (Opcionais)

| Parâmetro      | Tipo   | Descrição                                                  |
| -------------- | ------ | ---------------------------------------------------------- |
| start_date     | date   | Data inicial para filtrar compartilhamentos (padrão é início do mês atual) |
| end_date       | date   | Data final para filtrar compartilhamentos (padrão é fim do mês atual) |
| sender         | string | `email` ou `registration_id` do colaborador que enviou o reconhecimento |
| receiver       | string | `email` ou `registration_id` do colaborador que recebeu o reconhecimento |
| user_group_uuid| string | `uuid` do grupo de usuários para filtrar compartilhamentos. Consulte a [lista de grupos](/api/grupos-de-usuarios/ver-grupos) para obter os UUIDs disponíveis |

## Exemplo de Requisição

Para buscar compartilhamentos com filtros:

```
GET api/v2/recognitions/shares?start_date=01-01-2025&end_date=31-12-2025&receiver=joao.silva@empresa.com
```

Para buscar compartilhamentos por grupo de usuários:

```
GET api/v2/recognitions/shares?start_date=01-01-2025&end_date=31-12-2025&user_group_uuid=11111111-2222-3333-4444-555555555555
```

Para buscar todos os compartilhamentos:

```
GET api/v2/recognitions/shares
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-01-01",
        "end_date": "2025-12-31"
    },
    "shares": [
        {
            "recognition_date": "20/02/2025",
            "sender_name": "JACO BATALHA DE LIMA",
            "sender_email": "jaco.lima@empresa.com",
            "sender_registration_id": "000848",
            "receiver_name": "ALDNI DE OLIVEIRA BRAGA",
            "receiver_email": "aldni.braga@empresa.com",
            "receiver_registration_id": "000151",
            "message": "Parabéns pela excelente qualidade do trabalho realizado na produção. Sua dedicação e comprometimento com os resultados são exemplares.",
            "share_date": "20/02/2025",
            "social_channel": "WhatsApp"
        },
        {
            "recognition_date": "25/02/2025",
            "sender_name": "HELEN CRISTINA OLIVEIRA DA SILVA",
            "sender_email": "helen.cristina@empresa.com",
            "sender_registration_id": "001158",
            "receiver_name": "BYANCA MUNIZ MAIA",
            "receiver_email": "byanca.maia@empresa.com",
            "receiver_registration_id": "000684",
            "message": "Obrigada pelas valiosas dicas e pelo compartilhamento de conhecimento. É sempre uma experiência enriquecedora aprender com você.",
            "share_date": "25/02/2025",
            "social_channel": "Linkedin"
        },
        {
            "recognition_date": "06/03/2025",
            "sender_name": "GIOVANNI BONVICINI RAMOS",
            "sender_email": "giovanni.ramos@empresa.com",
            "sender_registration_id": "001258",
            "receiver_name": "DANIELE DIAS SOARES",
            "receiver_email": "daniele.soares@empresa.com",
            "receiver_registration_id": "001259",
            "message": "Muito obrigado pelo suporte durante o processo seletivo e integração. Sua abordagem humana e profissional foi fundamental para minha decisão de fazer parte da equipe.",
            "share_date": "06/03/2025",
            "social_channel": "Linkedin"
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
    "shares": [
        {
            "recognition_date": "15/03/2025",
            "sender_name": "ANTONIO SILVA",
            "sender_email": "antonio.silva@empresa.com",
            "sender_registration_id": "001200",
            "receiver_name": "BEATRIZ AMORIM",
            "receiver_email": "beatriz.amorim@empresa.com",
            "receiver_registration_id": "001201",
            "message": "Excelente trabalho na liderança da equipe. Sua capacidade de motivar e orientar os colaboradores é impressionante.",
            "share_date": "15/03/2025",
            "social_channel": "Facebook"
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
            "share_date": "22/06/2025",
            "social_channel": "Twitter"
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
