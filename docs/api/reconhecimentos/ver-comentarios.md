---
sidebar_position: 4
title: Ver comentários
---

# Ver comentários de reconhecimentos

Utilize esse método para buscar e visualizar os comentários feitos nos reconhecimentos dos colaboradores na plataforma.

## Método

**GET**
`api/v2/recognitions/comments`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Parâmetros

### Query Parameters (Opcionais)

| Parâmetro      | Tipo   | Descrição                                                  |
| -------------- | ------ | ---------------------------------------------------------- |
| start_date     | date   | Data inicial para filtrar comentários (padrão é início do mês atual) |
| end_date       | date   | Data final para filtrar comentários (padrão é fim do mês atual) |
| sender         | string | `email` ou `registration_id` do colaborador que enviou o reconhecimento |
| receiver       | string | `email` ou `registration_id` do colaborador que recebeu o reconhecimento |
| commenter      | string | `email` ou `registration_id` do colaborador que fez o comentário |
| user_group_uuid| string | `uuid` do grupo de usuários para filtrar comentários. Consulte a [lista de grupos](/api/grupos-de-usuarios/ver-grupos) para obter os UUIDs disponíveis |

## Exemplo de Requisição

Para buscar comentários com filtros:

```
GET api/v2/recognitions/comments?start_date=01-01-2024&end_date=31-01-2024&commenter=joao.silva@empresa.com
```

Para buscar comentários por grupo de usuários:

```
GET api/v2/recognitions/comments?start_date=01-01-2025&end_date=31-12-2025&user_group_uuid=11111111-2222-3333-4444-555555555555
```

Para buscar todos os comentários:

```
GET api/v2/recognitions/comments
```

## Resposta

### 200 - Sucesso

```json
{
    "filters": {
        "start_date": "2025-10-01",
        "end_date": "2025-10-31"
    },
    "comments": [
        {
            "recognition_date": "29/09/2025",
            "sender_name": "PAULO SILVA",
            "sender_email": "paulo.silva@empresa.com",
            "sender_registration_id": "000305",
            "receiver_name": "AMANDA SANTOS",
            "receiver_email": "amanda.santos@empresa.com",
            "receiver_registration_id": "001594",
            "message": "Boa tarde, Gostaria de lhe agradecer por sua agilidade e disponibilidade para suporte nas solicitações enviadas.",
            "comment_date": "02/10/2025",
            "commenter_name": "AMANDA SANTOS",
            "commenter_email": "amanda.santos@empresa.com",
            "commenter_registration_id": "001594",
            "comment_text": "Obrigada pelo reconhecimento, Paulo! Conte comigo 👊💯"
        },
        {
            "recognition_date": "30/09/2025",
            "sender_name": "MARCOS MENDES",
            "sender_email": "marcos.mendes@empresa.com",
            "sender_registration_id": "000354",
            "receiver_name": "LUCAS GONÇALVES",
            "receiver_email": "lucas.goncalves@empresa.com",
            "receiver_registration_id": "000771",
            "message": "Lucas passando para agradecer pela sua disponibilidade de mudança de horário, mesmo que foi temporariamente, para suprir uma demanda da produção, você não hesitou, mas viu realmente a necessidade que a empresa estava precisando naquele momento.",
            "comment_date": "01/10/2025",
            "commenter_name": "LUCAS GONÇALVES",
            "commenter_email": "lucas.goncalves@empresa.com",
            "commenter_registration_id": "000771",
            "comment_text": "Obrigado pelo reconhecimento marcos 👍"
        },
        {
            "recognition_date": "30/09/2025",
            "sender_name": "MARCOS MENDES",
            "sender_email": "marcos.mendes@empresa.com",
            "sender_registration_id": "000354",
            "receiver_name": "ALEF SANTOS",
            "receiver_email": "alef.santos@empresa.com",
            "receiver_registration_id": "001282",
            "message": "Alef quero agradecer pelo suporte que tem dado na produção, esclarecendo as dúvidas dos colaboradores, fazendo com que realizem suas atividades com mais segurança e qualidade.",
            "comment_date": "02/10/2025",
            "commenter_name": "ALEF SANTOS",
            "commenter_email": "alef.santos@empresa.com",
            "commenter_registration_id": "001282",
            "comment_text": "Obrigado, Marcos, pelo reconhecimento! Fico feliz em poder contribuir com a produção, dando suporte e ajudando a equipe a realizar as atividades com mais segurança e qualidade. 🙏"
        },
        {
            "recognition_date": "01/10/2025",
            "sender_name": "CARLOS OLIVEIRA",
            "sender_email": "carlos.oliveira@empresa.com",
            "sender_registration_id": "001100",
            "receiver_name": "MARIA COSTA",
            "receiver_email": "maria.costa@empresa.com",
            "receiver_registration_id": "001200",
            "message": "Maria, obrigado pela excelente apresentação no projeto. Sua organização e clareza foram fundamentais para o sucesso da reunião.",
            "comment_date": "02/10/2025",
            "commenter_name": "ANA RODRIGUES",
            "commenter_email": "ana.rodrigues@empresa.com",
            "commenter_registration_id": "001300",
            "comment_text": "Concordo totalmente! Maria sempre se destaca nas apresentações 🎯"
        },
        {
            "recognition_date": "02/10/2025",
            "sender_name": "FERNANDA LIMA",
            "sender_email": "fernanda.lima@empresa.com",
            "sender_registration_id": "001400",
            "receiver_name": "PEDRO BARBOSA",
            "receiver_email": "pedro.barbosa@empresa.com",
            "receiver_registration_id": "001500",
            "message": "Pedro, parabéns pela iniciativa em otimizar o processo de vendas. Sua visão estratégica trouxe resultados excelentes para a equipe.",
            "comment_date": "03/10/2025",
            "commenter_name": "ROBERTO ALMEIDA",
            "receiver_email": "roberto.almeida@empresa.com",
            "commenter_registration_id": "001600",
            "comment_text": "Realmente, Pedro sempre traz ideias inovadoras! 👏"
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
    "comments": [
        {
            "recognition_date": "15/03/2025",
            "sender_name": "ANTONIO CARLOS",
            "sender_email": "antonio.carlos@empresa.com",
            "sender_registration_id": "001200",
            "receiver_name": "BEATRIZ AMORIM",
            "receiver_email": "beatriz.amorim@empresa.com",
            "receiver_registration_id": "001201",
            "message": "Excelente trabalho no projeto de automação. Sua dedicação e conhecimento técnico foram fundamentais para o sucesso da implementação.",
            "comment_date": "16/03/2025",
            "commenter_name": "DIEGO SANTOS",
            "commenter_email": "diego.santos@empresa.com",
            "commenter_registration_id": "001202",
            "comment_text": "Parabéns Beatriz! Seu trabalho foi exemplar 🚀"
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
            "comment_date": "23/06/2025",
            "commenter_name": "GABRIELA SILVA",
            "commenter_email": "gabriela.silva@empresa.com",
            "commenter_registration_id": "001205",
            "comment_text": "Fábio sempre pensa no futuro da empresa! 💪"
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
            "comment_date": "11/09/2025",
            "commenter_name": "JESSICA ALMEIDA",
            "commenter_email": "jessica.almeida@empresa.com",
            "commenter_registration_id": "001208",
            "comment_text": "Igor é realmente um líder inspirador! 🌟"
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
            "comment_date": "06/11/2025",
            "commenter_name": "MARCOS OLIVEIRA",
            "commenter_email": "marcos.oliveira@empresa.com",
            "commenter_registration_id": "001211",
            "comment_text": "Larissa é nossa super-heroína! 🦸‍♀️"
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
            "comment_date": "19/12/2025",
            "commenter_name": "PAULA LIMA",
            "commenter_email": "paula.lima@empresa.com",
            "commenter_registration_id": "001214",
            "comment_text": "Oscar sempre entrega além das expectativas! 🎯"
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
  "error": "commenter not found"
}
```

Nesse caso, verifique se o email ou registration_id do usuário que fez o comentário está correto e existe no sistema.

```json
{
  "error": "user group not found"
}
```

Nesse caso, verifique se o UUID do grupo de usuários está correto e existe no sistema.
