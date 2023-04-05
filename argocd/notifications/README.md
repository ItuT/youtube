# notification

https://argocd-notifications.readthedocs.io/en/stable/

We take into account inaccuracies in the documentation on the site :)

## telegram chat
    
In the telegram, we are looking for the BotFather bot.

Create your own bot (/newbot). We get a token. We save it in secret.

In telegrams, create a group and add a bot to it.

From our user, we write a test message to the group.

We request information on the bot.

    curl https://api.telegram.org/botHERE_TOKEN/getUpdates

Looking for something like:

    "chat":{"id":-1009999999999,

This is the chat ID, which we will later substitute in the ConfigMap

## Configuration notification.

First, we create a secret in which we place the token.

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: argocd-notifications-secret
type: Opaque
stringData:
  telegram-token: "write the token here"
```
    
    kubectl -n argocd apply -f secret.yaml

Let's deploy the notification application.

* Or on the command line:

    kubectl -n argocd apply -f 00-rbac.yaml -f 01-configs.yaml -f 02-deployment.yaml

* or in ArgoCD 00-notification.yaml

## Link to video.

[<img src="https://img.youtube.com/vi/ayHXgjc0guM/maxresdefault.jpg" width="50%">](https://youtu.be/ayHXgjc0guM)
