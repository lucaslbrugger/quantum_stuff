# Quantum Stuff Group --- Manual de manutenção do site

Este repositório contém o site do **Quantum Stuff Group**, grupo de
pesquisa em Física da Universidade Federal de Juiz de Fora (UFJF).

O site é construído com **Hugo** e publicado automaticamente pelo
**GitHub Pages** usando **GitHub Actions**.

> **Objetivo deste documento:** permitir que outros professores,
> estudantes e futuros responsáveis pelo grupo consigam atualizar o site
> diretamente pelo GitHub, sem precisar conhecer Hugo ou programação em
> profundidade.

------------------------------------------------------------------------

## 1. Como o site funciona

A estrutura básica é:

``` text
quantum_stuff/
├── content/              ← textos e informações das páginas
├── layouts/              ← estrutura visual e funcionamento das páginas
├── assets/css/           ← estilos visuais
├── static/
│   └── images/           ← fotos e imagens
├── i18n/                 ← textos em português e inglês
├── .github/workflows/    ← publicação automática
├── hugo.toml             ← configuração principal
└── README.md             ← este manual
```

O fluxo de publicação é:

``` text
Alteração no GitHub
        ↓
Commit na branch main
        ↓
GitHub Actions
        ↓
Hugo gera o site
        ↓
GitHub Pages publica
```

**Não é necessário editar a pasta `public/`.** Ela é gerada
automaticamente pelo Hugo e está no `.gitignore`.

------------------------------------------------------------------------

# 2. Regra mais importante

Antes de editar qualquer coisa:

1.  Entre no repositório do grupo no GitHub.
2.  Confira se está na branch **`main`**.
3.  Faça apenas uma alteração por vez quando possível.
4.  Faça um commit com uma mensagem clara.
5.  Depois do commit, vá em **Actions** e confirme que o processo
    terminou com ✓ verde.

Exemplos de mensagens de commit:

``` text
Add photos from Fernando de Melo seminar
```

``` text
Update group member profile
```

``` text
Add new publication
```

``` text
Update research area
```

------------------------------------------------------------------------

# 3. Como fazer alterações diretamente pelo GitHub

É possível manter o site sem instalar nada no computador.

Para editar um arquivo:

1.  Abra o repositório no GitHub.
2.  Navegue até o arquivo.
3.  Clique no ícone de lápis **Edit this file**.
4.  Faça a alteração.
5.  Role até o final da página.
6.  Em **Commit changes**, escreva uma descrição curta.
7.  Clique em **Commit changes**.

Para adicionar uma imagem:

1.  Abra a pasta correspondente.
2.  Clique em **Add file → Upload files**.
3.  Selecione a imagem.
4.  Faça o commit.

Depois de qualquer alteração na branch `main`, o GitHub Actions tenta
publicar automaticamente o site.

------------------------------------------------------------------------

# 4. Galeria

As imagens da galeria ficam em:

``` text
static/images/gallery/
```

As informações exibidas na galeria ficam em:

``` text
content/gallery/_index.md
```

A versão em inglês fica em:

``` text
content/gallery/_index.en.md
```

## 4.1 Adicionar uma foto

Primeiro envie a imagem para:

``` text
static/images/gallery/
```

Use nomes simples, por exemplo:

``` text
fernando-melo-cbpf-01.jpg
fernando-melo-cbpf-02.jpg
```

Evite:

-   espaços;
-   acentos;
-   caracteres especiais;
-   nomes muito longos.

Depois edite:

``` text
content/gallery/_index.md
```

e adicione uma entrada:

``` yaml
images:
  - image: "images/gallery/fernando-melo-cbpf-01.jpg"
    title: "Seminário — Fernando de Melo (CBPF)"
    category: "Seminários"
    description: "Seminário de Fernando de Melo, do CBPF, realizado pelo Quantum Stuff Group."
```

Para adicionar duas fotos do mesmo evento:

``` yaml
images:
  - image: "images/gallery/fernando-melo-cbpf-01.jpg"
    title: "Seminário — Fernando de Melo (CBPF)"
    category: "Seminários"
    description: "Seminário de Fernando de Melo, do CBPF, realizado pelo Quantum Stuff Group."

  - image: "images/gallery/fernando-melo-cbpf-02.jpg"
    title: "Seminário — Fernando de Melo (CBPF)"
    category: "Seminários"
    description: "Seminário de Fernando de Melo, do CBPF, realizado pelo Quantum Stuff Group."
```

As duas fotos ficam na mesma categoria e possuem a mesma descrição.

### Importante

Se uma foto for apagada de:

``` text
static/images/gallery/
```

remova também sua entrada de:

``` text
content/gallery/_index.md
```

Caso contrário, a galeria tentará carregar uma imagem que não existe.

------------------------------------------------------------------------

# 5. Atividades e seminários

As atividades ficam em:

``` text
content/activities/
```

Cada atividade possui normalmente dois arquivos:

``` text
nome-da-atividade.md
nome-da-atividade.en.md
```

O primeiro é português e o segundo é inglês.

## 5.1 Criar uma nova atividade

Exemplo:

``` yaml
---
title: "Seminário — Fernando de Melo"
date: 2026-11-10
type: "Seminário"
speaker: "Fernando de Melo"
institution: "CBPF"
location: "UFJF"
description: "Seminário sobre ..."
---
```

A versão em inglês deve possuir o mesmo nome-base:

``` text
fernando-melo-10-11.md
fernando-melo-10-11.en.md
```

Exemplo em inglês:

``` yaml
---
title: "Seminar — Fernando de Melo"
date: 2026-11-10
type: "Seminar"
speaker: "Fernando de Melo"
institution: "CBPF"
location: "UFJF"
description: "Seminar on ..."
---
```

## 5.2 Como a agenda funciona

A página de atividades separa automaticamente:

-   atividades futuras;
-   atividades já realizadas.

A separação é feita pela data.

Portanto, **não é necessário mover uma atividade para outra seção quando
ela acontecer**.

Basta manter a data correta no front matter.

------------------------------------------------------------------------

# 6. Pessoas do grupo

As páginas dos integrantes ficam em:

``` text
content/people/
```

Cada pessoa possui uma versão em português e outra em inglês:

``` text
lucas-lauro-brugger.md
lucas-lauro-brugger.en.md
```

## 6.1 Estrutura de uma pessoa

Exemplo:

``` yaml
---
name: "Lucas Lauro Brugger"
role: "Doutorando"
short_bio: "Doutorando em fundamentos e informação quântica."
research:
  - "Informação Quântica"
  - "Fundamentos de Mecânica Quântica"
email: "lucasbrugger@estudante.ufjf.br"
scholar: "https://scholar.google.com/..."
lattes: "http://lattes.cnpq.br/..."
photo: "images/people/lucas-lauro-brugger.jpg"
---
```

A biografia completa fica abaixo do segundo `---`.

## 6.2 Adicionar a foto de uma pessoa

Envie a foto para:

``` text
static/images/people/
```

Depois use no front matter:

``` yaml
photo: "images/people/nome-do-arquivo.jpg"
```

Não coloque uma `/` no começo.

Correto:

``` yaml
photo: "images/people/lucas.jpg"
```

Evite:

``` yaml
photo: "/images/people/lucas.jpg"
```

## 6.3 Adicionar um novo integrante

1.  Envie a foto para `static/images/people/`.
2.  Crie:

``` text
content/people/nome-da-pessoa.md
```

3.  Crie também:

``` text
content/people/nome-da-pessoa.en.md
```

4.  Preencha as informações.
5.  Faça o commit.

A página de Pessoas organiza automaticamente os integrantes de acordo
com o `role`.

### Funções utilizadas atualmente

Português:

``` text
Professor
Professor Titular
Professor Convidado
Doutorando
Mestrando
IC
```

Inglês:

``` text
Professor
Full Professor
Invited Professor
PhD Student
Master's Student
Undergraduate Research Student
```

**Ao criar uma nova pessoa, prefira usar exatamente uma dessas
categorias**, para que ela apareça no grupo correto.

------------------------------------------------------------------------

# 7. Publicações

As publicações ficam em:

``` text
content/publications/
```

Assim como nas outras páginas, existem versões em português e inglês:

``` text
artigo.md
artigo.en.md
```

## 7.1 Estrutura básica

Exemplo:

``` yaml
---
title: "Título do artigo"
date: 2026-10-07
type: "Preprint"
authors:
  - "Nome Completo do Autor 1"
  - "Nome Completo do Autor 2"
journal: "arXiv:XXXX.XXXXX"
doi: "10.xxxx/xxxxx"
arxiv: "XXXX.XXXXX"
---
```

O resumo/abstract fica abaixo do segundo `---`.

## 7.2 DOI

Coloque apenas o identificador do DOI:

``` yaml
doi: "10.1007/s13538-024-01462-6"
```

Não coloque:

``` yaml
doi: "https://doi.org/10.1007/s13538-024-01462-6"
```

O site cria automaticamente o link correto.

## 7.3 arXiv

Coloque apenas o identificador:

``` yaml
arxiv: "2605.27424"
```

O site transforma automaticamente esse identificador no link do arXiv.

------------------------------------------------------------------------

# 8. Publicações relacionadas às pessoas

As páginas dos integrantes podem mostrar automaticamente as publicações
relacionadas.

Para isso, o nome do autor precisa corresponder ao campo `name` da
pessoa.

Exemplo da pessoa:

``` yaml
name: "Lucas Lauro Brugger"
```

Na publicação:

``` yaml
authors:
  - "Lucas Lauro Brugger"
  - "Bruno Ferreira Rizzuti"
```

O site consegue então associar a publicação ao perfil do Lucas e do
Bruno.

## Regra importante

Use os **nomes completos exatamente como aparecem no perfil da pessoa**.

Evite misturar:

``` text
Lucas L. Brugger
```

com:

``` text
Lucas Lauro Brugger
```

se o objetivo for fazer a associação automática.

Para autores externos ao grupo, abreviações podem ser mantidas quando o
nome completo não estiver disponível.

------------------------------------------------------------------------

# 9. Áreas de pesquisa

As áreas ficam em:

``` text
content/research/
```

Atualmente existem:

``` text
informacao-quantica.md
fundamentos-mecanica-quantica.md
fisica_aplicada.md
```

Cada área também possui uma versão:

``` text
arquivo.md
arquivo.en.md
```

Exemplo:

``` yaml
---
title: "Informação Quântica"
description: "Pesquisa em temas relacionados à teoria e informação quântica."
weight: 1
key: "quantum-information"
---
```

### Atenção ao `weight`

O `weight` controla a ordem das áreas.

Por exemplo:

``` yaml
weight: 1
```

aparece antes de:

``` yaml
weight: 2
```

Não altere o `key` sem necessidade, pois ele pode ser usado para
relacionar pesquisadores à área.

------------------------------------------------------------------------

# 10. Visitantes

As páginas de visitantes ficam em:

``` text
content/visitors/
```

As fotos ficam em:

``` text
static/images/visitors/
```

Exemplo:

``` yaml
---
title: "Nome do visitante"
institution: "Instituição"
country: "País"
date: 2026-10-07
photo: "images/visitors/nome.jpg"
---
```

Assim como nas outras seções, mantenha uma versão `.en.md` quando houver
conteúdo em inglês.

------------------------------------------------------------------------

# 11. Português e inglês

O site possui duas versões.

Arquivos em português:

``` text
arquivo.md
```

Arquivos em inglês:

``` text
arquivo.en.md
```

Por exemplo:

``` text
content/people/lucas-lauro-brugger.md
content/people/lucas-lauro-brugger.en.md
```

Se você adicionar uma nova página, **crie as duas versões** quando ela
precisar aparecer nos dois idiomas.

Os textos gerais da interface ficam em:

``` text
i18n/pt.yaml
i18n/en.yaml
```

Por exemplo:

``` yaml
"nav.publications": "Publicações"
```

e:

``` yaml
"nav.publications": "Publications"
```

### Atenção

Não altere uma chave existente em apenas um dos arquivos sem saber o que
está fazendo.

Se adicionar uma nova tradução, normalmente adicione a mesma chave nos
dois:

``` text
i18n/pt.yaml
i18n/en.yaml
```

------------------------------------------------------------------------

# 12. O que NÃO editar

### Não edite manualmente:

``` text
public/
resources/_gen/
```

Essas pastas são geradas pelo Hugo.

Também evite alterar:

``` text
.github/workflows/hugo.yml
```

sem conhecimento do funcionamento do GitHub Actions.

Esse arquivo controla a publicação automática do site.

------------------------------------------------------------------------

# 13. Como verificar se uma alteração foi publicada

Depois de fazer um commit na branch `main`:

1.  Abra o GitHub.
2.  Clique em **Actions**.
3.  Abra o workflow mais recente.
4.  Aguarde terminar.

Resultado esperado:

``` text
✓ Build and deploy Hugo site
```

Se estiver verde, a publicação terminou.

Se estiver vermelho:

1.  clique na execução;
2.  veja qual etapa falhou;
3.  não faça vários commits tentando corrigir sem identificar o erro.

------------------------------------------------------------------------

# 14. Se o site não atualizar

Primeiro:

### 1. Atualize o navegador

Use:

``` text
Ctrl + F5
```

Isso força uma atualização da página.

### 2. Confira o Actions

Veja se o workflow terminou com ✓ verde.

### 3. Confira os caminhos das imagens

Por exemplo:

Arquivo:

``` text
static/images/gallery/foto.jpg
```

deve ser referenciado como:

``` yaml
image: "images/gallery/foto.jpg"
```

### 4. Confira nomes de arquivos

Evite:

``` text
foto do grupo.jpg
```

Prefira:

``` text
foto-do-grupo.jpg
```

### 5. Confira YAML

Erros de indentação podem impedir o Hugo de construir o site.

Correto:

``` yaml
images:
  - image: "images/gallery/foto.jpg"
    title: "Título"
    category: "Grupo"
```

Incorreto:

``` yaml
images:
- image: "images/gallery/foto.jpg"
 title: "Título"
```

------------------------------------------------------------------------

# 15. Como desfazer uma alteração feita pelo GitHub

Se alguém fizer uma alteração errada, **não entre em pânico**.

O GitHub mantém o histórico de commits.

Abra:

``` text
Repository → Commits
```

Localize o commit responsável pela alteração.

É possível usar o histórico para identificar exatamente o que foi
modificado e restaurar a versão anterior.

Antes de apagar ou restaurar muitos arquivos, faça uma cópia local do
repositório ou peça ajuda a alguém que conheça Git.

------------------------------------------------------------------------

# 16. Manutenção recomendada

Para manter o site organizado:

### Imagens

Use:

``` text
nome-do-evento-01.jpg
nome-do-evento-02.jpg
```

### Pessoas

Use o nome completo e mantenha a mesma identificação nas versões PT/EN.

### Publicações

Use:

-   título completo;
-   autores em lista;
-   DOI sem `https://doi.org/`;
-   arXiv apenas com o identificador;
-   versão em português;
-   versão em inglês.

### Atividades

Sempre informe:

-   data;
-   título;
-   tipo;
-   palestrante;
-   instituição;
-   local;
-   descrição.

### Commits

Prefira mensagens claras:

``` text
Add new group member
```

``` text
Add seminar photos
```

``` text
Update publication information
```

``` text
Update activity schedule
```

------------------------------------------------------------------------

# 17. Estrutura rápida para consulta

  -----------------------------------------------------------------------
  O que quero alterar                 Onde alterar
  ----------------------------------- -----------------------------------
  Página inicial                      `content/_index.md` /
                                      `content/_index.en.md` e
                                      `layouts/index.html`

  Pessoas                             `content/people/`

  Fotos das pessoas                   `static/images/people/`

  Visitantes                          `content/visitors/`

  Fotos dos visitantes                `static/images/visitors/`

  Atividades                          `content/activities/`

  Publicações                         `content/publications/`

  Áreas de pesquisa                   `content/research/`

  Galeria                             `content/gallery/_index.md`

  Fotos da galeria                    `static/images/gallery/`

  Traduções da interface              `i18n/pt.yaml` e `i18n/en.yaml`

  Aparência/CSS                       `assets/css/main.css`

  Estrutura das páginas               `layouts/`

  Publicação automática               `.github/workflows/hugo.yml`

  Configuração do Hugo                `hugo.toml`
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 18. Para quem assumir o site no futuro

Se você estiver assumindo a manutenção do Quantum Stuff Group, o mais
importante é entender três coisas:

1.  **`content/` contém o conteúdo do site.**
2.  **`static/` contém as imagens e outros arquivos estáticos.**
3.  **`layouts/` e `assets/` controlam como o conteúdo aparece.**

Para a maioria das atualizações do dia a dia, você só precisará
trabalhar em:

``` text
content/
static/images/
i18n/
```

Não é necessário modificar os `layouts` para adicionar uma pessoa, uma
publicação, uma atividade ou uma fotografia.

Se uma alteração exigir mudança de layout ou funcionamento do site,
recomenda-se testar localmente com Hugo antes de publicar.

------------------------------------------------------------------------

# 19. Desenvolvimento local --- opcional

Para quem quiser trabalhar no computador em vez de editar diretamente
pelo GitHub, é possível instalar:

-   Git;
-   Hugo Extended;
-   Visual Studio Code.

Depois:

``` powershell
git clone https://github.com/lucaslbrugger/quantum_stuff.git
cd quantum_stuff
hugo server
```

O site local ficará disponível normalmente em:

``` text
http://localhost:1313/
```

As alterações podem ser testadas localmente antes de fazer o commit.

------------------------------------------------------------------------

## Resumo

Para uma atualização comum:

``` text
1. Edite ou adicione o arquivo no GitHub
        ↓
2. Commit changes
        ↓
3. GitHub Actions executa
        ↓
4. Hugo constrói o site
        ↓
5. GitHub Pages publica
        ↓
6. Confira o site
```

**Não é necessário fazer upload da pasta `public/`.**

O repositório é a fonte do site; o GitHub Actions é responsável por
gerar e publicar a versão final.
