# meu-bot-diego-app

O **meu-bot-diego-staging**: o [meu-bot](https://github.com/diegofornalha/meu-bot) com a página Módulos na frente e os
módulos do Diego (Salvy, Sendfy…). É um **app derivado**: este repositório guarda só a ficha e o ícone; o código é o do
meu-bot, e cada release daqui é o meu-bot da mesma versão empacotado com esta ficha.

- **Baixar:** a release mais recente em [Releases](https://github.com/diegofornalha/meu-bot-diego-app/releases). Depois
  de instalado, o app se atualiza sozinho a partir daqui.
- **Módulos:** não vêm no app. Ele os baixa do repositório do produto (`meu-bot-diego`, privado) com o acesso git de
  quem usa; sem acesso, a página diz "sem acesso aos módulos".
- **Para Mac com chip Apple.**

## O que tem aqui

```
produto.json        a ficha do app (nome, portas, página que abre na frente, onde saem as releases)
assets/icon.svg     o ícone, de origem
assets/icon.icns    o ícone que vai no app
```

Como um derivado funciona e como criar outro: [meu-bot-derivado-modelo](https://github.com/diegofornalha/meu-bot-derivado-modelo)
e o guia [docs/guia/derivados.md](https://github.com/diegofornalha/meu-bot/blob/main/docs/guia/derivados.md) do meu-bot.

Sugestão ou defeito do app em si vai para o [meu-bot](https://github.com/diegofornalha/meu-bot/issues): o código é de lá.
