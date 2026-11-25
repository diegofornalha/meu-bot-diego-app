# meu-bot-derivado-modelo

Modelo de um **app derivado do [meu-bot](https://github.com/diegofornalha/meu-bot)**: um meu-bot com nome, ícone, dados
e portas próprios, feito para uma pessoa ou um nicho.

O derivado **consome** o meu-bot (o core), não o copia. Este repositório guarda só o que é do derivado: a ficha e o
ícone. O código do app é o do core; quando o core melhora, o derivado recebe a melhoria na release seguinte.

## A regra

- O derivado não altera o core. Se ele precisar de algo que o core não oferece, a melhoria entra no core, para todos.
- O que nascer num derivado e servir a todos sobe para o core, e o derivado passa a usar o do core.
- Nada do derivado entra no repositório do core: nem linha na tabela de produtos, nem ícone.

## O que tem aqui

```
produto.json        a ficha do app
assets/icon.svg     o ícone, de origem
assets/icon.icns    o ícone que vai no app (gerado do .svg)
```

## Criar um derivado novo

1. **Crie o repositório a partir deste modelo** (público, para o app conseguir ler as próprias atualizações):

   ```bash
   gh repo create <dono>/meu-bot-<nome>-app --public --template diegofornalha/meu-bot-derivado-modelo --clone
   ```

2. **Preencha a ficha** (`produto.json`):

   | campo | o que pôr |
   |---|---|
   | `nome` | `meu-bot-<nome>-staging`: minúsculas, dígitos e hífen. É o nome do app, da pasta de dados e do link de login |
   | `bundleId` | `local.meu-bot-<nome>.staging`. Não muda depois que alguém instalar |
   | `canal` | `"staging"` (o único por enquanto) |
   | `portaLocal`, `portaWsl`, `portaMcp` | três números de 1024 a 65535 que nenhum outro app do meu-bot use no mesmo Mac |
   | `herdaDe` | `null`, ou `"meu-bot-staging"` para a primeira abertura copiar as configurações e conversas de lá |
   | `abreEm` | `null` (as conversas) ou `"modulos"` (a página Módulos na frente) |
   | `modulos` | `null`, ou o nome do produto de módulos do app (`meu-bot-<nome>`) |
   | `addon` | `null`, ou o add-on do catálogo do meu-bot que é a razão do app |
   | `releases` | `"<dono>/<este repositório>"`: onde saem as releases, e onde o app procura as atualizações |
   | `descricao` | uma frase sobre o app |

   Campo fora desta lista é recusado. O contrato completo está no guia do core:
   [docs/guia/derivados.md](https://github.com/diegofornalha/meu-bot/blob/main/docs/guia/derivados.md).

3. **Troque o ícone**: edite `assets/icon.svg` e gere o `.icns` (1024 × 1024).

4. **Confira a ficha**, de dentro de um checkout do core:

   ```bash
   npm run dist -- --produto <pasta deste repositório>
   ```

   Ficha recusada sai com o motivo. Aceita, o app é empacotado, assinado e instalado em `~/Applications`.

5. **Ligue a release automática**: no Mac que publica o meu-bot, acrescente o derivado à lista
   `~/Library/Application Support/meu-bot-release/derivados.json`:

   ```json
   [ { "repo": "<dono>/meu-bot-<nome>-app", "pasta": "/caminho/de/um/clone/só/do/agente" } ]
   ```

   Depois de cada release de teste do meu-bot, o derivado sai com a mesma versão nas releases deste repositório, e os
   apps instalados se atualizam sozinhos.

## O que um derivado não tem

- **Código próprio.** A ficha escolhe nome, portas e a página que abre na frente. Uma funcionalidade nova é proposta
  ao core.
- **Chave de assinatura própria.** O app só aceita atualização assinada com a chave e o certificado do meu-bot, então
  publicar um arquivo neste repositório não basta para um app instalado aceitá-lo.

## Este repositório

É só um modelo: o `meu-bot-exemplo-staging` da ficha não é publicado nem instalado por ninguém.
