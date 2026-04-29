# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projeto: Essenza — Blog de Gestão de Processos

Blog voltado para profissionais de gestão de processos, com conteúdo prático sobre BPM, melhoria contínua, automação e liderança operacional. Protótipo estático em HTML/CSS com plano de integração Firebase (sem Node.js).

## Preview Server

Configurado em `.claude/launch.json` com o nome `blog-gestao` na porta 3002. Para iniciar manualmente:

```bash
python -m http.server 3002 --directory blog-gestao
```

## Páginas

| Arquivo | Descrição | Status |
|---|---|---|
| `blog-gestao/index.html` | Homepage: navbar, hero, filtro de categorias, newsletter, footer (seção de artigos removida) | Completo |
| `blog-gestao/artigos.html` | Listagem de artigos com sidebar, busca e filtro por categoria | Completo |
| `blog-gestao/post.html` | Post individual com cover, conteúdo rico e metadados | Completo |
| `blog-gestao/login.html` | Tela de login/cadastro | Completo (sem backend) |
| `blog-gestao/sobre.html` | Página Sobre a autora: hero, especialidades, valores, CTA de contato | Completo |
| `blog-gestao/admin.html` | Painel admin para publicar posts | **A criar (Fase 2)** |
| `blog-gestao/style.css` | Estilos globais — usar variáveis CSS, nunca hardcodar cores | — |
| `blog-gestao/artigos.css` | Estilos específicos da página de artigos | — |

## Categorias do Blog

Processos · Operações · Pessoas · Indicadores · Melhoria Contínua · Tecnologia · Estratégia · Qualidade

## Conteúdo de Exemplo (homepage)

- Como mapear processos do zero *(Processos)*
- Os 7 desperdícios do Lean Manufacturing *(Melhoria Contínua)*
- KPIs essenciais para gestão de processos *(Indicadores)*
- RPA: quando automatizar *(Tecnologia)*
- Preparando para certificação ISO 9001:2015 *(Qualidade)*
- Cultura de melhoria contínua *(Pessoas)*

A seção de artigos em destaque foi removida da homepage. Os artigos ficam apenas na página `artigos.html`.

## Design System

Todas as cores são variáveis CSS em `:root` dentro de `style.css`. **Nunca usar valores hexadecimais diretamente no HTML ou CSS fora do `:root`.**

| Variável | Valor | Uso |
|---|---|---|
| `--primary` | `#2E7D9A` | Botões principais, links, tags, badge do hero |
| `--primary-dark` | `#256680` | Hover do botão primário |
| `--secondary` | `#5A8A6E` | Verde complementar |
| `--accent` | `#E8834A` | Botão da newsletter, CTAs secundários |
| `--bg` | `#F0F2F4` | Fundo geral da página |
| `--white` | `#FFFFFF` | Cards, navbar, hero |
| `--gray-light` | `#E8EAED` | Barra de categorias, fundos de seção |
| `--gray-mid` | `#D1D5DB` | Bordas de cards e navbar |
| `--text` | `#2D2D2D` | Texto principal |
| `--text-light` | `#6B7280` | Subtítulos, datas, metadados |
| `--border` | `#DDE1E7` | Bordas gerais |
| `--radius` | `12px` | Border-radius padrão de todos os cards |

**Fonte:** Inter (Google Fonts), pesos 300/400/500/600/700.

## Identidade Visual

- Logo: `Ess` em texto escuro + `enza` em `--primary`
- Navbar fixa no topo com sombra suave
- Hero em duas colunas: texto à esquerda, cards de destaque à direita
- Cards com hover de elevação (`translateY(-4px)`)
- Seção newsletter com fundo `--primary` e botão `--accent`
- Footer escuro (`#1a1a2e`) com logo em branco e `enza` em `--accent`

## Funcionalidades Implementadas

- Busca em tempo real na página de artigos
- Filtro por categoria (sidebar com 8 categorias)
- Grade de artigos 3 por linha
- Menu mobile com hamburger em todas as páginas (index, artigos, post, sobre)
- CSS do hamburger/menu mobile global em `style.css`
- Links do navbar corrigidos e padronizados em todas as páginas
- Novas páginas já herdam o padrão ao importar `style.css`

## Plano de Evolução

### Fase 1 — Design e Usabilidade (em andamento)

| # | Etapa | Status |
|---|---|---|
| 1 | Corrigir links do navbar | ✅ Concluído |
| 2 | Criar página Sobre (`sobre.html`) | ✅ Concluído |
| 3 | Menu mobile no `index.html` e `post.html` | ✅ Concluído |
| 4 | Implementar ordenação de artigos | Pendente |
| 5 | Botão "Carregar mais" na homepage | Pendente |

### GitHub

Repositório: https://github.com/vitoriacoelholrm-afk/essenza-blog
Site público: https://vitoriacoelholrm-afk.github.io/essenza-blog/blog-gestao/

### Fase 2 — Firebase (aguardando credenciais da usuária)

Login + banco de dados + painel admin via Firebase CDN (sem Node.js).
A usuária deve criar o projeto em firebase.google.com e colar o `firebaseConfig` no chat.

Estrutura de dados (Firestore — coleção `posts`): titulo, slug, resumo, conteudo, categoria, emoji, corFundo, autor, inicialAutor, publicado (bool), destaque (bool), criadoEm (timestamp).
