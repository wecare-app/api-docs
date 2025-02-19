---
sidebar_position: 10
---

# Desprogramar licença

Utilize esse método para desprogramar a licença de colaboradores.

O colaborador precisa ter licença programada para esse método ser utilizado.

## Método

**PATCH/PUT**
`api/v2/users/:key/unschedule_work_leave`

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
  "message": "A licença de Diego Oliveira foi desprogramada com sucesso!",
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
  "error": "Usuário não possui licença programada"
}
```

Nesse caso, o colaborador não possui licença programada. Primeiro [realize a programação de licença](/api/colaboradores/programar-licenca) para desprogramar.
