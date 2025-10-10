---
sidebar_position: 2
---

# Ver reconhecimentos

Utilize esse método para buscar e visualizar os reconhecimentos dos colaboradores na plataforma.

## Método

**GET**
`api/v2/recognitions`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

### Query Parameters (Opcionais)

| Parâmetro      | Tipo   | Descrição                                                  |
| -------------- | ------ | ---------------------------------------------------------- |
| start_date     | date   | Data inicial para filtrar reconhecimentos (padrão é início do mês atual) |
| end_date       | date   | Data final para filtrar reconhecimentos (padrão é fim do mês atual) |
| sender         | string | `email` ou `registration_id` do colaborador que enviou o reconhecimento |
| receiver       | string | `email` ou `registration_id` do colaborador que recebeu o reconhecimento |
| user_group_uuid| string | `uuid` do grupo de usuários para filtrar reconhecimentos. Consulte a [lista de grupos](/api/grupos-de-usuarios/ver-grupos) para obter os UUIDs disponíveis |

## Exemplo de Requisição

Para buscar reconhecimentos com filtros:

```
GET api/v2/recognitions?start_date=01-01-2024&end_date=31-01-2024&sender=joao.silva@empresa.com
```

Para buscar reconhecimentos por grupo de usuários:

```
GET api/v2/recognitions?start_date=01-01-2025&end_date=31-12-2025&user_group_uuid=11111111-2222-3333-4444-555555555555
```

Para buscar todos os reconhecimentos:

```
GET api/v2/recognitions
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-10-01",
        "end_date": "2025-10-31"
    },
    "recognitions": [
        {
            "date": "01/10/2025",
            "sender_name": "RAFAEL LIMA SOARES",
            "sender_email": "rafael.soares@empresa.com",
            "sender_registration_id": "001122",
            "sender_area_1": "SÃO PAULO",
            "sender_area_2": "LOGÍSTICA",
            "sender_area_3": "CARLOS EDUARDO ALMEIDA",
            "sender_manager_name": "MARCOS SILVEIRA",
            "sender_country": "BR",
            "receiver_name": "JULIANA TORRES ALMEIDA",
            "receiver_email": "juliana.almeida@empresa.com",
            "receiver_registration_id": "001123",
            "receiver_area_1": "SÃO PAULO",
            "receiver_area_2": "ADMINISTRAÇÃO",
            "receiver_area_3": "CARLOS EDUARDO ALMEIDA",
            "receiver_manager_name": "MARCOS SILVEIRA",
            "receiver_country": "BR",
            "virtue": "TRABALHO EM EQUIPE",
            "points": "50",
            "message": "Agradeço por todo o apoio desde o início. Parabéns pelos 5 anos de empresa e por sempre estar disposto a ajudar os colegas."
        },
        {
            "date": "01/10/2025",
            "sender_name": "MARTA FERNANDA SOUZA",
            "sender_email": "marta.souza@empresa.com",
            "sender_registration_id": "001124",
            "sender_area_1": "SÃO PAULO",
            "sender_area_2": "PRODUÇÃO",
            "sender_area_3": "CARLOS EDUARDO ALMEIDA",
            "sender_manager_name": "ANA CLARA MENDES",
            "sender_country": "BR",
            "receiver_name": "PEDRO HENRIQUE LOPES",
            "receiver_email": "pedro.lopes@empresa.com",
            "receiver_registration_id": "001125",
            "receiver_area_1": "SÃO PAULO",
            "receiver_area_2": "QUALIDADE",
            "receiver_area_3": "CARLOS EDUARDO ALMEIDA",
            "receiver_manager_name": "BRUNA RIBEIRO LIMA",
            "receiver_country": "BR",
            "virtue": "AÇÃO",
            "points": "25",
            "message": "Pedro, obrigado por estar sempre pronto para ajudar na resolução de problemas. Sua colaboração é essencial para a equipe."
        },
        {
            "date": "01/10/2025",
            "sender_name": "MARTA FERNANDA SOUZA",
            "sender_email": "marta.souza@empresa.com",
            "sender_registration_id": "001124",
            "sender_area_1": "SÃO PAULO",
            "sender_area_2": "PRODUÇÃO",
            "sender_area_3": "CARLOS EDUARDO ALMEIDA",
            "sender_manager_name": "ANA CLARA MENDES",
            "sender_country": "BR",
            "receiver_name": "CAMILA RODRIGUES PEREIRA",
            "receiver_email": "camila.pereira@empresa.com",
            "receiver_registration_id": "001126",
            "receiver_area_1": "SÃO PAULO",
            "receiver_area_2": "EMBALAGEM",
            "receiver_area_3": "CARLOS EDUARDO ALMEIDA",
            "receiver_manager_name": "ANA CLARA MENDES",
            "receiver_country": "BR",
            "virtue": "TRABALHO EM EQUIPE",
            "points": "50",
            "message": "Camila, parabéns pela sua dedicação e coragem. Obrigado por compartilhar seus conhecimentos e apoiar o time."
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
    "recognitions": [
        {
            "date": "02/01/2025",
            "sender_name": "BEATRIZ NOGUEIRA LIMA",
            "sender_email": "beatriz.lima@empresa.com",
            "sender_registration_id": "001216",
            "sender_area_1": "CENTRO DE DISTRIBUIÇÃO",
            "sender_area_2": "LOGÍSTICA",
            "sender_area_3": "CARLOS EDUARDO GOMES",
            "sender_manager_name": "POLLYANA MASSARANI",
            "sender_country": "BR",
            "receiver_name": "CAMILA QUEIROZ ALMEIDA",
            "receiver_email": "camila.queiroz@empresa.com",
            "receiver_registration_id": "000100",
            "receiver_area_1": "SEDE",
            "receiver_area_2": "ATENDIMENTO COMERCIAL",
            "receiver_area_3": "THOMAS BERNARDES",
            "receiver_manager_name": "SHEILA LIMA SANT'ANA",
            "receiver_country": "BR",
            "virtue": "AÇÃO",
            "points": "50",
            "message": "Muito obrigada por ser sempre prestativa, compartilhar conhecimento e manter alto nível de comprometimento. Excelente profissional!"
        },
        {
            "date": "05/01/2025",
            "sender_name": "PAULA FERREIRA ANDRADE",
            "sender_email": "paula.andrade@empresa.com",
            "sender_registration_id": "001001",
            "sender_area_1": "SÃO PAULO",
            "sender_area_2": "PRODUÇÃO",
            "sender_area_3": "PAULO HENRIQUE GOMES",
            "sender_manager_name": "MARINA LOPES FERREIRA",
            "sender_country": "BR",
            "receiver_name": "ANDRÉ OLIVEIRA NETO",
            "receiver_email": "andre.neto@empresa.com",
            "receiver_registration_id": "001419",
            "receiver_area_1": "SÃO PAULO",
            "receiver_area_2": "ALMOXARIFADO",
            "receiver_area_3": "PAULO HENRIQUE GOMES",
            "receiver_manager_name": "ADISON TEIXEIRA",
            "receiver_country": "BR",
            "virtue": "AÇÃO",
            "points": "50",
            "message": "Profissional ágil, atento aos detalhes e sempre disposto a entregar o melhor. Exemplo de pessoa de ação."
        },
        {
            "date": "05/01/2025",
            "sender_name": "PAULA FERREIRA ANDRADE",
            "sender_email": "paula.andrade@empresa.com",
            "sender_registration_id": "001001",
            "sender_area_1": "SÃO PAULO",
            "sender_area_2": "PRODUÇÃO",
            "sender_area_3": "PAULO HENRIQUE GOMES",
            "sender_manager_name": "MARINA LOPES FERREIRA",
            "sender_country": "BR",
            "receiver_name": "ROSANA BRITO SOUZA",
            "receiver_email": "rosana.souza@empresa.com",
            "receiver_registration_id": "001149",
            "receiver_area_1": "SÃO PAULO",
            "receiver_area_2": "PRODUÇÃO",
            "receiver_area_3": "PAULO HENRIQUE GOMES",
            "receiver_manager_name": "MARINA LOPES FERREIRA",
            "receiver_country": "BR",
            "virtue": "TRABALHO EM EQUIPE",
            "points": "50",
            "message": "Entrega seu trabalho com antecedência e está sempre disposta a apoiar quem precisa, com foco no resultado do time."
        },
        {
            "date": "10/01/2025",
            "sender_name": "DANIEL VARGAS PIRES",
            "sender_email": "daniel.pires@empresa.com",
            "sender_registration_id": "001602",
            "sender_area_1": "SEDE",
            "sender_area_2": "NOVOS NEGÓCIOS",
            "sender_area_3": "PATRÍCIA SANTOS",
            "sender_manager_name": "PATRÍCIA SANTOS",
            "sender_country": "BR",
            "receiver_name": "GUSTAVO PEREIRA DOS SANTOS",
            "receiver_email": "gustavo.pereira@empresa.com",
            "receiver_registration_id": "001934",
            "receiver_area_1": "PLANTA 2",
            "receiver_area_2": "QUALIDADE",
            "receiver_area_3": "LUIZ CARVALHO COSTA",
            "receiver_manager_name": "THALITA MARQUES",
            "receiver_country": "BR",
            "virtue": "TRABALHO EM EQUIPE",
            "points": "40",
            "message": "Agradeço o suporte nos testes com o novo produto. A prontidão demonstrou excelente parceria entre as áreas!"
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
