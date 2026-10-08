# Acme Dashboard — Next.js Learn (App Router)

Dashboard financeiro construído ao longo do curso oficial
[Next.js Learn — App Router](https://nextjs.org/learn/dashboard-app), com
evolução registrada capítulo a capítulo.

> Status: em construção — capítulos 1 a 3 concluídos.

## Demo

- Local: http://localhost:3000
- Produção (Vercel): _em breve — deploy previsto após o capítulo 6_

## Stack

| Tecnologia | Uso |
| --- | --- |
| Next.js 16 (App Router + Turbopack) | Framework full-stack |
| React 19 | UI |
| Tailwind CSS 3 + CSS Modules | Estilização |
| `next/font` (Inter + Lusitana) | Fontes otimizadas |
| Postgres (`postgres` lib) | Banco de dados (a partir do cap. 6) |
| NextAuth.js v5 (beta) | Autenticação (a partir do cap. 15) |
| pnpm | Gerenciador de pacotes |

## Progresso no curso

- [x] **1 — Getting Started** — scaffold, `pnpm install`, `pnpm dev`
- [x] **2 — CSS Styling** — `global.css` no layout raiz, Tailwind, exercício
      de CSS Modules (`app/ui/home.module.css`)
- [x] **3 — Optimizing Fonts and Images** — `Inter`/`Lusitana` via
      `next/font`, hero images com `next/image`
- [ ] **4 — Creating Layouts and Pages** — rotas `/dashboard/*` e `/login`
- [ ] **5 — Linking and Navigating**
- [ ] **6 — Setting Up Your Database** — Postgres na Vercel + seed
- [ ] **7 — Fetching Data**
- [ ] **8 — Static and Dynamic Rendering**
- [ ] **9 — Streaming**
- [ ] **10 — Partial Prerendering**
- [ ] **11 — Adding Search and Pagination**
- [ ] **12 — Mutating Data**
- [ ] **13 — Handling Errors**
- [ ] **14 — Improving Accessibility**
- [ ] **15 — Adding Authentication**
- [ ] **16 — Adding Metadata**

## Como rodar

Pré-requisitos: Node.js 20.9+ e pnpm.

```bash
cd nextjs-dashboard
cp .env.example .env   # preencha POSTGRES_URL a partir do cap. 6
pnpm install
pnpm dev               # http://localhost:3000
```

Chegagens úteis:

```bash
pnpm exec tsc --noEmit  # typecheck deve passar zerado
```

Banco de dados (cap. 6 em diante):

```bash
# com o POSTGRES_URL configurado, popular o banco:
# abra http://localhost:3000/seed no navegador
```

## Estrutura

```text
app/
├── page.tsx          # home pública
├── layout.tsx        # layout raiz (fonte + estilos globais)
├── lib/              # definições, acesso a dados, utils, seed data
├── query/            # rota de teste (cap. 7)
├── seed/             # rota de seed do banco (cap. 6)
└── ui/               # componentes (sidenav, tabelas, formulários, ...)
public/               # hero images, clientes, favicon
```

## Notas técnicas

- O acesso ao Postgres é lazy (`getSql()` em `app/lib/data.ts`): sem
  `POSTGRES_URL` o dev não quebra — as queries falham com mensagem clara.
- `GET /login` retorna 404 nesta fase; a página chega no capítulo 4.

## Autor

Leonardo Coutinho Cunha — projeto de estudos documentado capítulo a capítulo.
