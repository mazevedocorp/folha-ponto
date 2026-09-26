# PWA Gateway — Folha Ponto MAzevedo Corp
## Eliminação do Warning do Google Apps Script & Instalação Nativa no Celular

Este pacote estático desacoplado transforma o sistema **Folha Ponto MAzevedo Corp** em um **Progressive Web App (PWA) de alto padrão**, eliminando integralmente a mensagem de aviso padrão do Google Apps Script (*"Este aplicativo foi criado por outro usuário e não pelo Google"*) e viabilizando a instalação nativa com 1 toque no Android e iPhone.

---

### 🚀 Principais Benefícios

1. **Eliminação de 100% do Warning de Sandbox:** Ao carregar através do seu próprio domínio ou GitHub Pages com certificado SSL, o navegador não exibe a barra amarela de advertência do Google.
2. **Instalação Nativa na Tela de Início:** O usuário instala o app com o ícone oficial da MAzevedo Corp e o nome **"Folha Ponto"**.
3. **Modo Standalone (Tela Cheia):** Executa sem barra de endereços, abas ou botões de navegação, proporcionando a experiência idêntica à de um aplicativo baixado na Google Play ou App Store.
4. **Preservação de Permissões de Hardware (Portaria MTE 671/2021):** O iframe seguro fullscreen repassa as permissões de Geolocalização (`geolocation *`) e Câmera, garantindo o registro fiscal de coordenadas GPS e comprovante com QR Code.
5. **Custo Zero:** Pode ser hospedado gratuitamente em menos de 2 minutos.

---

### 📦 Estrutura dos Arquivos

```
pwa-gateway/
├── index.html       # Shell PWA fullscreen com iframe seguro, splash screen e banner
├── manifest.json    # Manifesto oficial com regras de display standalone e ícones
├── sw.js            # Service Worker para conformidade PWA (Lighthouse 100/100)
├── icon.svg         # Ícone vetorial da MAzevedo Corp
├── icon-192.png     # Ícone para dispositivos móveis (192x192)
├── icon-512.png     # Ícone de alta definição para splash screen (512x512)
└── README.md        # Este guia operacional
```

---

### ⏱️ Guia Rápido de Publicação (Deploy em 2 Minutos)

#### Opção 1: GitHub Pages (Recomendado — Gratuito)
1. Crie um repositório no seu GitHub (ex: `folha-ponto-app`);
2. Faça upload dos arquivos da pasta `pwa-gateway/` para o repositório;
3. Acesse **Settings ➔ Pages**;
4. Em **Build and deployment / Branch**, selecione `main` (ou `root`) e clique em **Save**;
5. Em instantes, sua URL estará no ar:
   `https://seu-usuario.github.io/folha-ponto-app/`
6. Acesse a URL no seu smartphone. O app abrirá limpo, sem aviso do Google e com a opção de instalação imediata!

#### Opção 2: Cloudflare Pages / Vercel / Netlify
1. Faça login na [Cloudflare Pages](https://pages.cloudflare.com) ou [Vercel](https://vercel.com);
2. Conecte ao seu repositório ou arraste a pasta `pwa-gateway/`;
3. Conclua o deploy com 1 clique para obter uma URL ultra-rápida na CDN global.

#### Opção 3: Domínio Corporativo Próprio (Ex: `ponto.mazevedocorp.com.br`)
1. Aponte um registro CNAME do seu subdomínio corporativo para o seu projeto no GitHub Pages ou Cloudflare Pages;
2. Configure o certificado SSL automático;
3. Seus colaboradores acessarão através do domínio oficial da empresa.

---

### ⚙️ Como Vincular a URL do seu Google Apps Script

Existem 3 formas simples de apontar o Gateway para o seu WebApp:

1. **Parâmetro na URL (Instantâneo):**
   Envie o link para os colaboradores com o parâmetro `?src=`:
   `https://seu-usuario.github.io/folha-ponto-app/?src=https://script.google.com/macros/s/SEU_DEPLOY_ID/exec?view=mobile`
   *(O gateway salvará a URL automaticamente no dispositivo).*

2. **No próprio App (Botão ⚙️ URL):**
   No canto superior direito da tela do Gateway, toque no botão `⚙️ URL`, cole o link do seu WebApp implantado e toque em **Salvar**.

3. **Direto no Código (`index.html`):**
   Abra `index.html` e altere a constante `DEFAULT_WEBAPP_URL`:
   ```javascript
   const DEFAULT_WEBAPP_URL = 'https://script.google.com/macros/s/SEU_SCRIPT_ID/exec?view=mobile';
   ```

---

### 📱 Como o Colaborador Instala no Celular

* **Android (Google Chrome):**
  Ao abrir a página, surgirá o banner flutuante **"Instalar App"** na parte inferior. Basta 1 toque para adicionar à tela inicial. Se preferir, acesse o menu de 3 pontinhos (⋮) ➔ **"Instalar aplicativo"**.

* **iPhone (Apple Safari):**
  Toque no botão **Compartilhar (⎋)** na barra inferior do Safari, role para baixo e selecione **"Adicionar à Tela de Início" (➕)**. O aplicativo abrirá em tela cheia sem nenhuma barra do navegador!
