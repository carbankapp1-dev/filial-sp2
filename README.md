# Car Bank — Prévia (Filial GO/TO)

Site estático (HTML + JS) com PWA, usando **Firebase Realtime Database** como backend.
Pronto para publicar no **GitHub Pages**.

## Arquivos
- `index.html` — a aplicação inteira
- `manifest.json` — configuração do PWA
- `sw.js` — service worker (cache offline)
- `android-chrome-192x192.png` / `android-chrome-512x512.png` — ícones

Os caminhos internos foram ajustados para **relativos**, então funciona tanto num
domínio próprio quanto num link do tipo `seuusuario.github.io/nome-do-repo/`.

## Passo a passo para publicar

### 1. Criar o repositório
1. Acesse https://github.com/new
2. Dê um nome, por exemplo `carbank-previa` (repositório **público**)
3. Não marque "Add a README" (já temos um)
4. Clique em **Create repository**

### 2. Subir os arquivos
**Opção A — pela interface web (mais simples):**
1. Na página do repositório recém-criado, clique em **"uploading an existing file"**
2. Arraste os 5 arquivos deste pacote (`index.html`, `manifest.json`, `sw.js`, os dois `.png`)
3. Clique em **Commit changes**

**Opção B — pelo terminal (git):**
```bash
git init
git add .
git commit -m "Migração inicial do Netlify"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/carbank-previa.git
git push -u origin main
```

### 3. Ativar o GitHub Pages
1. No repositório, vá em **Settings → Pages**
2. Em "Build and deployment" → "Source", escolha **Deploy from a branch**
3. Branch: `main`, pasta: `/ (root)`
4. Clique em **Save**
5. Aguarde 1–2 minutos. O link ficará assim:
   `https://SEU_USUARIO.github.io/carbank-previa/`

### 4. (Opcional) Domínio próprio
Se quiser manter o mesmo endereço que você usava no Netlify, adicione um
domínio customizado em **Settings → Pages → Custom domain**, e configure um
registro CNAME apontando para `SEU_USUARIO.github.io` no seu provedor de DNS.

## Sobre o Firebase
Nenhuma mudança é necessária no Firebase — ele já funciona 100% no navegador
(client-side), independente de onde o HTML está hospedado. A `apiKey` visível
no código **não é um segredo**; a segurança dos dados é feita pelas regras do
Firebase Realtime Database (Firebase Console → Realtime Database → Rules).
Vale a pena conferir se essas regras estão restritas ao necessário, já que o
repositório será público.

## Observação sobre o repositório público
Como o repositório é público, qualquer pessoa poderá ver o código-fonte
(incluindo a senha de admin `@1234`, que está fixa no JavaScript). Se isso for
um problema, considere:
- Trocar o repositório para **privado** (mas atenção: no plano **Free**, o
  GitHub Pages só funciona com repositórios **públicos**; publicar a partir de
  um repositório privado exige o plano **Pro** ou superior), ou
- Mover a validação de senha para as regras do Firebase, em vez de deixá-la
  fixa no código.
