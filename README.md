# Sistema de Documentos — Exército Brasileiro (RP)

Gerador de advertências, exonerações e promoções para a corporação Exército
Brasileiro. Documentos são desenhados em `<canvas>` e podem ser baixados em PNG
ou enviados direto para um canal do Discord.

**Uso exclusivo de roleplay.** Os documentos gerados são fictícios e não têm
qualquer valor oficial — o rodapé de cada imagem diz isso explicitamente.

## Arquivos

Um arquivo só: `index.html`. Sem build, sem dependências, sem servidor.
A única coisa externa são as fontes do Google Fonts.

## Como publicar no GitHub Pages

1. Crie um repositório novo no GitHub (público).
2. Suba o `index.html` na raiz do repositório.
3. No repositório: **Settings → Pages**.
4. Em *Build and deployment*, escolha **Deploy from a branch**, branch `main`,
   pasta `/ (root)`, e clique em **Save**.
5. Um ou dois minutos depois o site fica no ar em
   `https://<usuario>.github.io/<repositorio>/`.

Cada `git push` novo republica o site automaticamente.

## Webhook do Discord

Por padrão o site vem **sem webhook fixo**: cada pessoa clica na etiqueta
"WEBHOOK NÃO CONFIGURADO" (canto superior direito), cola a URL do webhook e ela
fica salva só no navegador dela (`localStorage`).

Se preferir deixar fixo para todo mundo, preencha as constantes no topo do
`<script>` do `index.html`:

```js
const WEBHOOK_URL       = "https://discord.com/api/webhooks/...";
const PROMO_WEBHOOK_URL = "";   // vazio = usa o mesmo canal acima
```

> Atenção: o código de um site no GitHub Pages é público. Uma URL de webhook
> escrita ali pode ser lida por qualquer visitante, que passa a conseguir postar
> mensagens no seu canal. Se isso acontecer, apague o webhook no Discord e crie
> outro.

Como criar o webhook: Discord → botão direito no canal → **Editar canal** →
**Integrações** → **Webhooks** → **Novo webhook** → **Copiar URL do webhook**.

## Personalização rápida

Tudo fica no topo do `<script>` do `index.html`:

- `NOME_UNIDADE` / `SIGLA_UNIDADE` — texto do cabeçalho do documento.
- `PATENTES` — lista de postos e graduações usada em todos os menus suspensos.
  Edite para bater com a hierarquia da sua cidade.

As cores ficam no bloco `:root` do `<style>`:

| Variável   | Uso                                  |
|------------|--------------------------------------|
| `--olive`  | verde-oliva principal (botões, selo) |
| `--gold`   | dourado (abas, títulos, moldura)     |
| `--paper`  | cor do papel do documento            |
| `--bg`     | fundo do painel                      |
