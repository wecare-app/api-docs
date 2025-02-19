---
sidebar_position: 4
---

# Desprogramar bloqueio

Utilize esse método para desprogramar o bloqueio de colaboradores.

O colaborador precisa ter um bloqueio programado para esse método ser utilizado.

## Método

**PATCH/PUT**
`api/v2/users/:key/cancel_block`

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

## Requisição

A requisição não necessita de um `body`.

## Resposta

### 200

```json
{
  "message": "Bloqueio do(a) colaborador Diego Oliveira dos Santos desprogramado",
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
    "status": "active"
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
  "error": "O(A) colaborador não possui bloqueio programado"
}
```

Nesse caso, o colaborador não possui nenhum bloqueio programado. Primeiro [realize o bloqueio](/api/colaboradores/bloquear-colaborador), para então conseguir utilizar esse método.
