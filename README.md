# SoulSurfers — Landing Page

Landing page responsiva do **soulsurfers.com.br**, com os pilares lifestyle, comunidade, marca/loja e conteúdo/viagens.

## Requisitos
- Node.js 20+ (recomendado 22)
- npm
- Conta GitHub e Cloudflare

## Rodar localmente
```bash
npm install
npm run dev
```

## Gerar a versão de produção
```bash
npm run build
npm run preview
```

## Publicar com Cloudflare Workers Builds (GitHub)
1. No GitHub, utilize este repositório `gutoAI/soulsurfers-landing` na branch `main`.
2. Cloudflare Dashboard > Workers & Pages > Create > Import a repository / Connect to Git (a nomenclatura pode variar).
3. Selecione o repositório e branch `main`.
4. Build command: `npm run build`.
5. Deploy command: `npx wrangler deploy` (ou `npm run deploy` quando a plataforma não executar build previamente).
6. Root directory: `/` (raiz do repositório). Configuração `wrangler.jsonc` já inclui `assets.directory = ./dist`.
7. Após publicar, em Worker > Settings > Domains & Routes, conecte o domínio personalizado `soulsurfers.com.br` e depois `www.soulsurfers.com.br`, definindo redirecionamento canônico no painel se necessário.
8. Se a zona DNS não estiver na Cloudflare, siga o procedimento de inclusão da zona e troca de nameservers indicado no painel. Confira registros MX/TXT antes de alterá-los para não quebrar e-mail.

## Publicar manualmente pela CLI
```bash
npm install
npx wrangler login
npm run deploy
```

## Estado funcional desta versão
- ✅ Navegação por âncoras, menu mobile, metadados SEO, Open Graph, layout responsivo, CSS e animações.
- ✅ HTML/CSS/React/Vite e configuração para Workers static assets.
- ⚠️ Newsletter: abre o cliente de e-mail do visitante (`mailto:contato@soulsurfers.com.br`). **Não salva assinantes.** É necessário criar e configurar a caixa postal e uma API de cadastro antes de anunciar captação real.
- ⚠️ Loja, comunidade e viagens são seções editoriais de pré-lançamento, sem checkout, login, reservas ou artigos publicados.
- ⚠️ Fotos do Unsplash são carregadas de URLs externas. Para autonomia e performance máxima, substitua por arquivos licenciados e hospedados em `public/images`. Verifique os direitos/licenças antes de uso comercial definitivo.
- ⚠️ O domínio só ficará online após vinculação de GitHub/Cloudflare e configuração DNS; o ZIP sozinho não publica a página.

## Ajustes fáceis
- Textos e fotos: `src/main.jsx`.
- Cores, tipografia e espaçamento: `src/styles.css`.
- Título e SEO: `index.html`.
- Nome Worker e assets: `wrangler.jsonc`.

## Fontes técnicas
- https://developers.cloudflare.com/workers/static-assets/
- https://developers.cloudflare.com/workers/framework-guides/web-apps/react/
- https://developers.cloudflare.com/workers/configuration/routing/custom-domains/
