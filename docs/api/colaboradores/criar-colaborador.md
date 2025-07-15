---
sidebar_position: 1
---

# Criar colaborador

Utilize esse método para criar novos colaboradores na plataforma.

## Método

**POST**
`api/v2/users`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Atributos

### Obrigatórios

| Atributos | Tipo   | Descrição                                                                  |
| --------- | ------ | -------------------------------------------------------------------------- |
| name      | string | Nome do colaborador                                                        |
| email     | string | Email do colaborador, obrigatório somente se a matrícula não for informada |
| matricula | string | Matrícula do colaborador, obrigatória somente se o email não for informado |

### Opcionais

| Atributos      | Tipo   | Descrição                                                  |
| -------------- | ------ | ---------------------------------------------------------- |
| manager        | string | Email ou matrícula do gestor do colaborador                |
| cellphone      | string | Número de telefone celular do colaborador, incluindo o DDD |
| birth_date     | date   | Data de nascimento do colaborador no formato DD/MM/YYYY    |
| function       | string | Cargo do colaborador                                       |
| admission_date | date   | Data de admissão do colaborador no formato DD/MM/YYYY      |
| company_area_1 | string | Área nível 1 do colaborador (Ex: diretoria)                |
| company_area_2 | string | Área nível 2 do colaborador (Ex: gerência)                 |
| company_area_3 | string | Área nível 3 do colaborador (Ex: equipe)                   |

## Requisição

```json
{
  "user": {
    "name": "Diego Oliveira",
    "email": "diegooliveira@email.com",
    "registration_id": "10010234",
    "function": "Desenvolvedor Backend SR",
    "company_area_1": "Produto",
    "company_area_2": "Desenvolvimento",
    "company_area_3": "Backend",
    "cellphone": "61 99999 9999",
    "birth_date": "01/01/2000",
    "admission_date": "01/01/2022",
    "manager": "tiagodossantos@email.com"
  }
}
```

## Resposta

### 201

```json
{
  "message": "user created",
  "user": {
    "admission_date": "01/01/2022",
    "area": {
      "level_1": "Produto",
      "level_2": "Desenvolvimento",
      "level_3": "Backend"
    },
    "birth_date": "01/01/2000",
    "cellphone": "61999999999",
    "email": "diegooliveira@email.com",
    "function": "Desenvolvedor Backend SR",
    "manager": {
      "name": "Tiago dos Santos",
      "email": "tiagodossantos@email.com",
      "registration_id": "00010234"
    },
    "name": "Diego Oliveira",
    "registration_id": "10010234"
  }
}
```

### 401

```json
{
  "error": "access token expired"
}
```

Nesse caso, verifique se o `access_token` no header `Authorization` está correto.

### 422

```json
{
  "error": "user already registered"
}
```

Nesse caso, o colaborador já foi cadastro. Atualize seu cadastro utilizando o método [Atualizar colaborador](/api/colaboradores/atualizar-colaborador).

```json
{
  "error": "email cannot be blank"
}
```

Nesse caso, o email é obrigatório por ser a chave.

```json
{
  "error": "registration id cannot be blank"
}
```

Nesse caso, a matrícula é obrigatória por ser a chave.

```json
{
  "error": "leader of the user not found"
}
```

Nesse caso, a liderança informada não está cadastrada. Realize primeiro o cadastro da liderança e torne a criar o colaborador.

## Envio em lote

:::info[Disponibilidade da funcionalidade]
O envio em lote está disponível, no momento, apenas para o ambiente de Homologação da WeCare.
:::

Para criar mais de um colaborador por vez, realize a requisição dessa forma:

```json
{
  "users": [
    {
      "user": {
        // parâmetros de user
      },
      "user": {
        // parâmetros de user
      },
      ...
    }
  ]
}
```
