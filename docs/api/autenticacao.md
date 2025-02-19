---
slug: /api/autenticacao
sidebar_position: 2
---

# Autenticação

A autenticação é realizada através das chaves de API `key` e `secret` fornecidas pela WeCare.

## Método

**POST**
`api/v2/authenticate`

## Atributos

### Obrigatórios

| Atributos | Tipo   | Descrição        |
| --------- | ------ | ---------------- |
| key       | string | Chave da empresa |
| secret    | string | Senha da empresa |

## Requisição

```json
{
  "key": "95a07b70-57e4-454e-926f-65549fb91f30",
  "secret": "9790cdb4-a17e-4bc8-a936-0e9b97942f47"
}
```

## Resposta

### 200

Utilize o `access_token` no header `Authorization` nas próximas requisições.

```json
{
  "acccess_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJqdGkiOiJhNWZjOGIxZS1kYzFiLTRhMTktYmQxNC04OWZkZjUxYjJlOWYiLCJleHAiOjE3MTcwMTA2ODUsImlhdCI6MTcxNzAwMzQ4NSwidXVpZCI6IjE1ZDMzY2E1LWM1N2UtNDc0Ni1hNWQzLWEwYTNjNGIzMmUzYSJ9.Kfgo9d6XEAE--AAt0w5i5Mz2NJG0lF0CVouf1dC_o7Q"
}
```

### 401

Nesse caso, verifique se as credenciais que informou estão válidas. Caso contrário, solicite novas credenciais à equipe de TI da WeCare.

```json
{
  "error": "invalid credentials"
}
```
