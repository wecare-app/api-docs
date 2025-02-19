---
sidebar_position: 6
---

# Desligar colaborador

Utilize esse método para desligar colaboradores na plataforma.

**ATENÇÃO**: Esse método desliga os colaboradores de forma imediata. Essa ação só é reversível pela plataforma.

## Método

**DELETE**
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

## Requisição

A requisição não necessita de um `body`.

## Resposta

### 200

```json
{
  "message": "Colaborador Diego Oliveira dos Santos desligado(a)"
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
