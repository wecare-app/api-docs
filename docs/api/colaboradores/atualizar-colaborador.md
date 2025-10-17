---
sidebar_position: 2
---

# Atualizar colaborador

Utilize esse método para atualizar colaboradores na plataforma.

## Método

**PATCH/PUT**
`api/v2/users/:key`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Atributos

### Obrigatórios

| Atributos | Tipo   | Descrição                                                   |
| --------- | ------ | ----------------------------------------------------------- |
| key       | string | Chave do colaborador usada no cadastro (email ou matrícula) |

### Opcionais

| Atributos      | Tipo   | Descrição                                                                  |
| -------------- | ------ | -------------------------------------------------------------------------- |
| name           | string | Nome do colaborador                                                        |
| email          | string | Email do colaborador, obrigatório somente se a matrícula não for informada |
| registration_id| string | Matrícula do colaborador, obrigatória somente se o email não for informado |
| manager        | string | Email ou matrícula do gestor do colaborador                                |
| cellphone      | string | Número de telefone celular do colaborador, incluindo o DDD                 |
| birth_date     | date   | Data de nascimento do colaborador no formato DD/MM/YYYY                    |
| function       | string | Cargo do colaborador                                                       |
| admission_date | date   | Data de admissão do colaborador no formato DD/MM/YYYY                      |
| company_area_1 | string | Área nível 1 do colaborador (Ex: diretoria)                                |
| company_area_2 | string | Área nível 2 do colaborador (Ex: gerência)                                 |
| company_area_3 | string | Área nível 3 do colaborador (Ex: equipe)                                   |

## Requisição

```json
{
  "user": {
    "name": "Diego Oliveira dos Santos",
    "function": "Desenvolvedor Frontend PL",
    "company_area_1": "Produto",
    "company_area_2": "Desenvolvimento",
    "company_area_3": "Frontend",
    "cellphone": "61 98989 9898"
  }
}
```

## Resposta

### 200

```json
{
  "message": "user updated",
  "user": {
    "admission_date": "01/01/2022",
    "area": {
      "level_1": "Produto",
      "level_2": "Desenvolvimento",
      "level_3": "Frontend"
    },
    "birth_date": "01/01/2000",
    "cellphone": "61989899898",
    "email": "diegooliveira@email.com",
    "function": "Desenvolvedor Frontend PL",
    "manager": {
      "name": "Tiago dos Santos",
      "email": "tiagodossantos@email.com",
      "registration_id": "10010234"
    },
    "name": "Diego Oliveira dos Santos",
    "registration_id": "00010234"
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

### 404

```json
{
  "error": "user not found"
}
```

Nesse caso, não existe colaborador para a chave informada.

### 422

```json
{
  "error": "email already exists"
}
```

Nesse caso, o email informado já está cadastrado em outro colaborador.

```json
{
  "error": "registration_id already exists"
}
```

Nesse caso, a matrícula já está cadastrada em outro colaborador.

```json
{
  "error": "leader of the user not found"
}
```

Nesse caso, a liderança informada não está cadastrada. Realize primeiro o cadastro da liderança e torne a criar o colaborador.

## Envio em lote

Para atualizar mais de um colaborador por vez, realize a requisição dessa forma:

```json
{
  "users": [
    {
      "key": {
        // parâmetros de user
      },
    },
    {
      "key": {
        // parâmetros de user
      }
    },
    ...
  ]
}
```

Não envie o parâmetro `key` na URL do endpoint. Use o endpoint abaixo:

**PATCH/PUT**
`api/v2/users`
