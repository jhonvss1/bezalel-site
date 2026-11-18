# Bezalel — site

Página estática única. Sem build, sem dependências. Fontes (Fraunces e Inter) vêm do Google Fonts.

## Arquivos

- `index.html`: a página inteira (CSS dentro dela)
- `og.png`: imagem de prévia (1200x630) que aparece quando o link é compartilhado
- `robots.txt` e `sitemap.xml`: para o Google
- Em todos eles, `DOMINIO` é um marcador. Troque pelo domínio real antes de publicar.

## 1. Trocar o marcador do domínio

Exemplo com `bezalel.dev` (Git Bash, dentro desta pasta):

```bash
sed -i 's/DOMINIO/bezalel.dev/g' index.html robots.txt sitemap.xml
```

No PowerShell:

```powershell
Get-ChildItem index.html, robots.txt, sitemap.xml | ForEach-Object {
  (Get-Content $_ -Raw -Encoding utf8) -replace 'DOMINIO', 'bezalel.dev' | Set-Content $_ -Encoding utf8
}
```

## 2. Publicar no Cloudflare Pages

1. Crie um repositório novo no GitHub só para esta pasta (por exemplo `bezalel-site`). Não use o repositório do Braggo.
2. No painel do Cloudflare: Workers e Pages, Create, Pages, Connect to Git, escolha o repositório.
3. Framework preset: None. Build command: vazio. Build output directory: `/`.
4. Ao terminar, o site fica em `nome-do-projeto.pages.dev`. Confira antes de ligar o domínio.

Alternativa sem Git: em Pages, Upload assets, e arraste esta pasta.

## 3. Ligar o domínio próprio

No projeto do Pages: Custom domains, Set up a domain. Se o domínio estiver no Registro.br, aponte os DNS para o Cloudflare ou crie o registro CNAME que o painel indicar. O HTTPS é automático.

## 4. Google

1. Abra o Google Search Console e adicione o domínio.
2. Envie `https://SEU-DOMINIO/sitemap.xml` em Sitemaps.
3. Em Inspeção de URL, cole a página inicial e peça indexação.
4. Coloque o link do site no perfil do GitHub e do LinkedIn. Links de fora ajudam o Google a achar e confiar na página.

A página costuma aparecer em alguns dias, às vezes em semanas.

## Pendências

- Seção "Projetos próprios" removida de propósito, porque ainda não há projeto publicado além do Braggo. Quando o primeiro sair, voltam a seção, o item do menu e o texto do hero sobre projetos próprios.
- Depois de publicar, teste a prévia do link colando o endereço no LinkedIn Post Inspector. WhatsApp e LinkedIn guardam a prévia em cache, então demora a atualizar se você mudar a imagem.
