---
sidebar_position: 7
---

# Programar férias

Utilize esse método para programar férias para colaboradores na plataforma.

## Método

**PATCH/PUT**
`api/v2/users/:key/schedule_vacation`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Atributos

### Obrigatórios

| Atributos      | Tipo   | Descrição                                                   |
| -------------- | ------ | ----------------------------------------------------------- |
| key            | string | Chave do colaborador usada no cadastro (email ou matrícula) |
| vacation_start | string | Data de início das férias (formato `dd/mm/aaaa`)            |
| vacation_end   | string | Data de fim das férias (formato `dd/mm/aaaa`)               |

## Requisição

```json
{
  "vacation_start": "01/01/2022",
  "vacation_end": "10/01/2022"
}
```

## Resposta

### 200

```json
{
  "message": "As férias de Diego Oliveira foram programadas com sucesso!",
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
    "registration_id": "10010234",
    "status": "active",
    "vacation_start": "01/01/2022",
    "vacation_end": "10/01/2022"
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
  "error": "A data de início das férias deve ser maior ou igual a hoje"
}
```

Nesse caso, a data de início das férias deve ser maior ou igual a data atual.

```json
{
  "error": "A data de término das férias deve ser maior ou igual a data de início"
}
```

Nesse caso, a data de término das férias deve ser maior ou igual a data de início das férias.
