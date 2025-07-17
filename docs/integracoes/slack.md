---
sidebar_position: 2
---

# Slack

A WeCare disponibiliza um bot para notificações em conversas privadas no Slack. Para disponibilizar essa integração aos seus colaboradores, siga os próximos passos.

## Configuração do Bot em seu Workspace do Slack

Acesse o [ambiente de gestão de aplicativos do Slack](https://api.slack.com/apps/) e clique no botão **Create New App**.

![](/img/integracoes/slack/slack-1.png)

Selecione a opção **From a manifest**.

![](/img/integracoes/slack/slack-2.png)

Nessa primeira etapa, selecione o Workspace da sua organização, essa opção não pode ser modificada posteriormente. Após isso, clique no botão **Next**.

![](/img/integracoes/slack/slack-3.png)

Nessa etapa, copie e cole o JSON abaixo e clique no botão **Next**.

```json
{
  "display_information": {
    "name": "WeCare Bot",
    "description": "Notificações da plataforma",
    "background_color": "#2c3f51"
  },
  "features": {
    "aplicativo_home": {
      "home_tab_enabled": true,
      "messages_tab_enabled": false,
      "messages_tab_read_only_enabled": false
    },
    "bot_user": {
      "display_name": "WeCare Bot",
      "always_online": true
    }
  },
  "oauth_config": {
    "scopes": {
      "bot": [
        "chat:write",
        "users:read",
        "users.profile:read",
        "incoming-webhook"
      ]
    }
  },
  "settings": {
    "interactivity": {
      "is_enabled": true,
      "request_url": "https://www.wecare.aplicativo.br/slack/webhook"
    },
    "org_deploy_enabled": false,
    "socket_mode_enabled": false,
    "token_rotation_enabled": false
  }
}
```

![](/img/integracoes/slack/slack-4.png)

Nessa última etapa, confirme as configurações do aplicativo.

![](/img/integracoes/slack/slack-5.png)

Com o aplicativo criado, é necessário fazer a instalação dele em seu Workspace. Clique para instalar.

![](/img/integracoes/slack/slack-6.png)

Confirme as permissões e selecione algum canal para o WeCare Bot postar mensagens. A princípio nosso Bot não envia mensagens em canais públicos e privados, apenas em mensagens diretas. Você pode criar um canal apenas para o Bot.

![](/img/integracoes/slack/slack-7.png)

Ao instalar o aplicativo, você terá acesso ao **token oAuth**. Copie-o, ele será utilizado pela plataforma da WeCare para enviar mensagens através do seu Bot para o seu Workspace.

![](/img/integracoes/slack/slack-8.png)

Em Settings > Basic Information, você pode modificar o nome, cores, ícone e descrição do aplicativo para ficar a cara da sua empresa.

![](/img/integracoes/slack/slack-9.png)

A configuração está concluída! ✨

Encaminhe para o time de TI da WeCare o **token oAuth**.

A ativação do Bot pelo colaborador é explicada em nossa plataforma no menu lateral **Vincular Slack**.
