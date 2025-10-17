---
sidebar_position: 3
title: Ver curtidas
---

# Ver curtidas de reconhecimentos

Utilize esse método para buscar e visualizar as curtidas dados aos reconhecimentos dos colaboradores na plataforma.

## Método

**GET**
`api/v2/recognitions/likes`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

### Query Parameters (Opcionais)

| Parâmetro      | Tipo   | Descrição                                                  |
| -------------- | ------ | ---------------------------------------------------------- |
| start_date     | date   | Data inicial para filtrar curtidas (padrão é início do mês atual) |
| end_date       | date   | Data final para filtrar curtidas (padrão é fim do mês atual) |
| sender         | string | `email` ou `registration_id` do colaborador que enviou o reconhecimento |
| receiver       | string | `email` ou `registration_id` do colaborador que recebeu o reconhecimento |
| liker          | string | `email` ou `registration_id` do colaborador que deu a curtida |
| user_group_uuid| string | `uuid` do grupo de usuários para filtrar curtidas. Consulte a [lista de grupos](/api/grupos-de-usuarios/ver-grupos) para obter os UUIDs disponíveis |

## Exemplo de Requisição

Para buscar curtidas com filtros:

```
GET api/v2/recognitions/likes?start_date=01-01-2024&end_date=31-01-2024&liker=joao.silva@empresa.com
```

Para buscar curtidas por grupo de usuários:

```
GET api/v2/recognitions/likes?start_date=01-01-2025&end_date=31-12-2025&user_group_uuid=11111111-2222-3333-4444-555555555555
```

Para buscar todos as curtidas:

```
GET api/v2/recognitions/likes
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-10-01",
        "end_date": "2025-10-31"
    },
    "likes": [
        {
            "recognition_date": "19/09/2025",
            "sender_name": "JOÃO SILVA",
            "sender_email": "joao.silva@empresa.com",
            "sender_registration_id": "001141",
            "receiver_name": "MARIA SANTOS",
            "receiver_email": "maria.santos@empresa.com",
            "receiver_registration_id": "001217",
            "message": "Queria agradecer a você por ter me ajudado até agora com os projetos que temos em comum, dando apoio e suporte para realizarmos todas etapas dentro dos prazos.",
            "like_date": "01/10/2025",
            "liker_name": "PEDRO OLIVEIRA",
            "liker_email": "pedro.oliveira@empresa.com",
            "liker_registration_id": "000556"
        },
        {
            "recognition_date": "29/09/2025",
            "sender_name": "ANA COSTA",
            "sender_email": "ana.costa@empresa.com",
            "sender_registration_id": "000305",
            "receiver_name": "CARLOS MENDES",
            "receiver_email": "carlos.mendes@empresa.com",
            "receiver_registration_id": "001595",
            "message": "Boa tarde, Gostaria de agradecer por todo o apoio e pelas ações relacionadas à emissão de notas fiscais e ao ajuste de cadastro, tanto de fornecedores quanto de produtos. Sua agilidade e comprometimento fazem a diferença para a equipe.",
            "like_date": "01/10/2025",
            "liker_name": "PEDRO OLIVEIRA",
            "liker_email": "pedro.oliveira@empresa.com",
            "liker_registration_id": "000556"
        },
        {
            "recognition_date": "29/09/2025",
            "sender_name": "FERNANDA LIMA",
            "sender_email": "fernanda.lima@empresa.com",
            "sender_registration_id": "000646",
            "receiver_name": "ROBERTO ALMEIDA",
            "receiver_email": "roberto.almeida@empresa.com",
            "receiver_registration_id": "001169",
            "message": "Durante o projeto, você se destacou muito demonstrando trabalho em equipe, tendo a iniciativa de entender o fluxo do processo afim de apoiar na resolução do problema o mais rápido possível e garantir o funcionamento da operação. Parabéns pela iniciativa e a disposição quando sempre precisamos do seu apoio.",
            "like_date": "02/10/2025",
            "liker_name": "JULIANA RODRIGUES",
            "liker_email": "juliana.rodrigues@empresa.com",
            "liker_registration_id": "000410"
        },
        {
            "recognition_date": "30/09/2025",
            "sender_name": "LUCAS PEREIRA",
            "sender_email": "lucas.pereira@empresa.com",
            "sender_registration_id": "001273",
            "receiver_name": "CAMILA SOUZA",
            "receiver_email": "camila.souza@empresa.com",
            "receiver_registration_id": "001082",
            "message": "Gostaria de agradecer por aceitar o convite para a minha reunião mensal e por compartilhar suas ideias e conhecimentos. Sua participação e interesse ficaram evidentes e agregaram muito ao nosso encontro.",
            "like_date": "02/10/2025",
            "liker_name": "JULIANA RODRIGUES",
            "liker_email": "juliana.rodrigues@empresa.com",
            "liker_registration_id": "000410"
        },
        {
            "recognition_date": "30/09/2025",
            "sender_name": "LUCAS PEREIRA",
            "sender_email": "lucas.pereira@empresa.com",
            "sender_registration_id": "001273",
            "receiver_name": "CARLOS MENDES",
            "receiver_email": "carlos.mendes@empresa.com",
            "receiver_registration_id": "001595",
            "message": "Quero te reconhecer pelo o seu empenho em solucionar problemas com cadastros de clientes, o seu comprometimento é fundamental para o crescimento da empresa. A sua maestria para solucionar problemas é notória.",
            "like_date": "01/10/2025",
            "liker_name": "PEDRO OLIVEIRA",
            "liker_email": "pedro.oliveira@empresa.com",
            "liker_registration_id": "000556"
        },
        {
            "recognition_date": "30/09/2025",
            "sender_name": "PATRICIA FERREIRA",
            "sender_email": "patricia.ferreira@empresa.com",
            "sender_registration_id": "000684",
            "receiver_name": "RICARDO BARBOSA",
            "receiver_email": "ricardo.barbosa@empresa.com",
            "receiver_registration_id": "000839",
            "message": "O trabalho em equipe faz toda diferença, sempre atenta na qualidade do produto, comunicativa com a parte operacional, age com responsabilidade e ética, sempre buscando a melhoria do processo. Parabéns por agir com agilidade e ter a comunicação precisa.",
            "like_date": "03/10/2025",
            "liker_name": "VANESSA MARTINS",
            "liker_email": "vanessa.martins@empresa.com",
            "liker_registration_id": "001118"
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
    "likes": [
        {
            "recognition_date": "15/03/2025",
            "sender_name": "ANTONIO CARLOS",
            "sender_email": "antonio.carlos@empresa.com",
            "sender_registration_id": "001200",
            "receiver_name": "BEATRIZ AMORIM",
            "receiver_email": "beatriz.amorim@empresa.com",
            "receiver_registration_id": "001201",
            "message": "Excelente trabalho no projeto de automação. Sua dedicação e conhecimento técnico foram fundamentais para o sucesso da implementação.",
            "like_date": "16/03/2025",
            "liker_name": "DIEGO SANTOS",
            "liker_email": "diego.santos@empresa.com",
            "liker_registration_id": "001202"
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
            "like_date": "23/06/2025",
            "liker_name": "GABRIELA SILVA",
            "liker_email": "gabriela.silva@empresa.com",
            "liker_registration_id": "001205"
        },
        {
            "recognition_date": "10/09/2025",
            "sender_name": "HELENA RODRIGUES",
            "sender_email": "helena.rodrigues@empresa.com",
            "sender_registration_id": "001206",
            "receiver_name": "IGOR PEREIRA",
            "receiver_email": "igor.pereira@empresa.com",
            "receiver_registration_id": "001207",
            "message": "Obrigado pelo suporte constante e pela paciência ao ensinar os novos membros da equipe. Você é um exemplo de liderança.",
            "like_date": "11/09/2025",
            "liker_name": "JESSICA ALMEIDA",
            "liker_email": "jessica.almeida@empresa.com",
            "liker_registration_id": "001208"
        },
        {
            "recognition_date": "05/11/2025",
            "sender_name": "KEVIN BARBOSA",
            "sender_email": "kevin.barbosa@empresa.com",
            "sender_registration_id": "001209",
            "receiver_name": "LARISSA FERREIRA",
            "receiver_email": "larissa.ferreira@empresa.com",
            "receiver_registration_id": "001210",
            "message": "Sua capacidade de resolver problemas complexos e manter a calma sob pressão é impressionante. Obrigado por sempre estar disponível.",
            "like_date": "06/11/2025",
            "liker_name": "MARCOS OLIVEIRA",
            "liker_email": "marcos.oliveira@empresa.com",
            "liker_registration_id": "001211"
        },
        {
            "recognition_date": "18/12/2025",
            "sender_name": "NATALIA SOUZA",
            "sender_email": "natalia.souza@empresa.com",
            "sender_registration_id": "001212",
            "receiver_name": "OSCAR MENDES",
            "receiver_email": "oscar.mendes@empresa.com",
            "receiver_registration_id": "001213",
            "message": "Parabéns pelo excelente trabalho no fechamento do ano. Sua organização e atenção aos detalhes foram essenciais para o sucesso.",
            "like_date": "19/12/2025",
            "liker_name": "PAULA LIMA",
            "liker_email": "paula.lima@empresa.com",
            "liker_registration_id": "001214"
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
  "error": "liker not found"
}
```

Nesse caso, verifique se o email ou registration_id do usuário que deu a curtida está correto e existe no sistema.

```json
{
  "error": "user group not found"
}
```

Nesse caso, verifique se o UUID do grupo de usuários está correto e existe no sistema.
