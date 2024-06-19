---
sidebar_position: 3
---

# Bloquear colaborador

Utilize esse método para bloquear colaboradores na plataforma.

Você pode bloquear um colaborador numa data específica e também especificar uma data para desbloquear automaticamente.

Caso não especifique uma data, o colaborador será bloqueado imediatamente.

## Método

**PATCH/PUT**
`api/v2/users/:key/block`

## Headers

| Header        | Valor               |
| ------------- | ------------------- |
| Authorization | Bearer access_token |

Obtenha o `access_token` pelo [método de autenticação](/).

## Atributos

### Obrigatórios

| Atributos | Tipo   | Descrição                                                   |
| --------- | ------ | ----------------------------------------------------------- |
| key       | string | Chave do colaborador usada no cadastro (email ou matrícula) |

### Opcionais

| Atributos     | Tipo | Descrição                              |
| ------------- | ---- | -------------------------------------- |
| blocked_at    | date | Data de bloqueio no formato DD/MM/YYYY |
| blocked_until | date | Data de bloqueio no formato DD/MM/YYYY |

## Requisição

```json
{}
```

## Resposta

### 200

```json
{
  "message": "Colaborador Diego Oliveira dos Santos bloqueado(a)",
  "user": {
    "admission_date": "01/01/2022",
    "area": {
      "level_1": "Produto",
      "level_2": "Desenvolvimento",
      "level_3": "Frontend"
    },
    "birth_date": "01/01/2000",
    "blocked_at": "18/06/2024",
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
    "status": "blocked"
  }
}
```

## Requisição

```json
{
  "blocked_at": "20/06/2024",
  "blocked_until": "20/07/2024"
}
```

## Resposta

### 200

```json
{
  "message": "Colaborador Diego Oliveira dos Santos será bloqueado(a) em 20/06/2024",
  "user": {
    "admission_date": "01/01/2022",
    "area": {
      "level_1": "Produto",
      "level_2": "Desenvolvimento",
      "level_3": "Frontend"
    },
    "birth_date": "01/01/2000",
    "blocked_until": "20/07/2024",
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
    "status": "pending"
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
  "error": "O(A) colaborador já está bloqueado(a)"
}
```

Nesse caso, o colaborador já foi bloqueado.

```json
{
  "error": "A data de bloqueio não pode ser anterior à data atual"
}
```

Nesse caso, a data de bloqueio deve ser maior que o dia atual. Caso queira bloquear o colaborador imediatamente, não informe a data de bloqueio.

```json
{
  "error": "A data de desbloqueio não pode ser anterior à data de bloqueio"
}
```

Nesse caso, a data de desbloqueio deve ser maior que a data de bloqueio. Caso não queira desbloquear o colaborador não informe a data de desbloqueio.

```json
{
  "error": "A data de bloqueio não pode ser igual à data de desbloqueio"
}
```

Nesse caso, a data de desbloqueio deve ser maior que a data de bloqueio em 1 dia ou mais. Caso não queira desbloquear o colaborador não informe a data de desbloqueio.
