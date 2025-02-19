---
sidebar_position: 8
---

# Programar licença

Utilize esse método para programar licença para colaboradores na plataforma.

## Método

**PATCH/PUT**
`api/v2/users/:key/schedule_work_leave`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/api/autenticacao).

## Atributos

### Obrigatórios

| Atributos        | Tipo   | Descrição                                                   |
| ---------------- | ------ | ----------------------------------------------------------- |
| key              | string | Chave do colaborador usada no cadastro (email ou matrícula) |
| work_leave_start | string | Data de início da licença (formato `dd/mm/aaaa`)            |

### Opcionais

| Atributos      | Tipo   | Descrição                                         |
| -------------- | ------ | ------------------------------------------------- |
| work_leave_end | string | Data de término da licença (formato `dd/mm/aaaa`) |

## Requisição

```json
{
  "work_leave_start": "01/01/2022",
  "work_leave_end": "10/01/2022"
}
```

## Resposta

### 200

```json
{
  "message": "A licença de Diego Oliveira foi programada com sucesso!",
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
    "function": "Desenvolvedor Backend SR",
    "manager": {
      "name": "Tiago dos Santos",
      "email": "tiagodossantos@email.com",
      "registration_id": "10010234"
    },
    "name": "Diego Oliveira",
    "registration_id": "10010234",
    "status": "active",
    "work_leave_end": "10/01/2022",
    "work_leave_start": "01/01/2022"
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
  "error": "A data de início da licença deve ser maior ou igual a data atual"
}
```

Nesse caso, a data de início da licença deve ser maior ou igual a data atual.

```json
{
  "error": "A data de término da licença deve ser maior ou igual a data de início"
}
```

Nesse caso, a data de término da licença deve ser maior ou igual a data de início da licença.
