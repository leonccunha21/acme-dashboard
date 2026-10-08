# Contexto do Projeto — retomar conversa em nova sessão

> Se você (assistente) está lendo isto numa sessão nova: o usuário moveu o
> projeto de pasta manualmente e esta é a continuação da conversa anterior.
> Leia este arquivo e siga a partir de "Plano".

## O projeto
- **O quê:** Dashboard financeiro do curso oficial Next.js Learn ("App Router" —
  https://nextjs.org/learn/dashboard-app).
- **Pasta nova (após move manual):**
  `G:\Meu Drive\Academia ZM — Desenvolvimento & IA\03 — Projetos e exercícios\Aula\nextjs-dashboard`
- **Pasta antiga:** `C:\Users\Leo\Documents\Aula\nextjs-dashboard`
- **Stack:** Next.js 16.0.10 (Turbopack), React 19, Tailwind 3.4, Postgres
  (`postgres` lib), next-auth 5 beta (instalado, ainda não usado), pnpm.
- **Rodar:** `pnpm dev` dentro de `nextjs-dashboard/` → http://localhost:3000.
- **Typecheck:** `pnpm exec tsc --noEmit` (deve passar zerado).

## Papel do assistente
- O usuário está estudando o curso e me designou como **guia a partir do
  capítulo 2 (CSS Styling)**.
- Combinado: ele lê cada capítulo e pratica; eu reviso o código, tiro dúvidas
  e só então avançamos ao próximo capítulo. Ir capítulo por capítulo, sem
  pular para a solução final do tutorial.

## Estado atual (até 08/10/2026)
- Capítulo 2 lido pelo usuário (pendente ele confirmar conclusão).
- Capítulo 3 ainda não iniciado formalmente.
- `pnpm dev` sobe limpo (200 na `/`) e `tsc --noEmit` passa sem erros.

## Correções já aplicadas (não refazer)
1. `app/ui/fonts.ts` — CRIADO (`Inter` + `Lusitana` via `next/font/google`).
   Era a causa de 7 erros TS (`@/app/ui/fonts` não existia).
2. `app/layout.tsx` — importa `@/app/ui/global.css`, usa `inter`, tem
   `metadata` (cap. 2 + parte do cap. 3).
3. `app/page.tsx` — `AcmeLogo` descomentado + hero images
   (`/hero-desktop.png`, `/hero-mobile.png`) com `next/image` (cap. 3).
4. `pnpm-workspace.yaml` — `bcrypt`/`sharp` estavam como texto
   `"set this to true or false"`; corrigidos para `true`.
5. `next.config.ts` — mantido padrão (sem `turbopack.root`; removi tentativa
   com `__dirname` porque quebra em config ESM).
6. `app/lib/data.ts` — conexão Postgres virou lazy via `getSql()` (antes
   conectava no import com `POSTGRES_URL!` e derrubava o dev sem `.env`).
7. `app/seed/route.ts` — mesmo padrão lazy; `GET` reescrito (o original usava
   `sql.begin` com array de promises, incorreto; agora faz seed sequencial e
   retorna erro como string).
8. `.env` — criado a partir do `.env.example` (valores VAZIOS, só placeholder).
9. Removidos `C:\Users\Leo\Documents\Aula\pnpm-lock.yaml` e
   `C:\Users\Leo\Documents\Aula\node_modules` (lixo de `pnpm install` na pasta
   errada que causava o warning de múltiplos lockfiles no Turbopack).

## Pendências / próximos passos
- [ ] Usuário confirma leitura do cap. 2 → revisar e tirar dúvidas.
- [ ] Guiar cap. 3 (Optimizing Fonts and Images) — checar o que já está ok.
- [ ] Cap. 4+: criar rotas `/dashboard/*` e `/login`, `auth.ts`, `actions.ts`
      (componentes UI já existem em `app/ui/`; as páginas ainda não).
- [ ] Preencher `POSTGRES_URL` etc. no `.env` e rodar `/seed` (cap. 6 do curso).
- [ ] Exercício opcional do cap. 2 (triângulo Tailwind vs `home.module.css`)
      foi pulado de propósito — é demonstrativo, não manter no código.
- [ ] Avisos não-bloqueantes no log do dev: `baseline-browser-mapping` e
      `caniuse-lite` desatualizados (só atualizar se incomodar).
- [ ] Atenção: projeto agora vive numa pasta sincronizada do Google Drive —
      `node_modules`/`.next` com milhares de arquivos podem deixar o sync
      lento; se der problema, considerar mover `node_modules` para fora do
      sync ou pausar o Drive durante `pnpm install`.

## Atualização 08/10/2026 (madrugada)
- Tentativa de mover `Aula` para o Google Drive foi interrompida no meio e
  dividiu os arquivos entre C: e G:. Situação resolvida: projeto completo e
  verificado em `C:\Users\Leo\Documents\Aula\nextjs-dashboard`.
- Cópia (quase completa, sem `public/`) existe em
  `G:\Meu Drive\Academia ZM — Desenvolvimento & IA\03 — Projetos e exercícios\Aula\`
  — NÃO usar como base sem antes copiar `public/` e limpar lixos
  (`_tmp_*`, `node_modules`/`package.json`/`pnpm-lock.yaml` da raiz `Aula`).
- `node_modules` do C: estava corrompido (faltava `next/font`); reinstalado.
- `app/ui/home.module.css` criado com a classe `.shape` do cap. 2.
- `tsc --noEmit` zerado, `pnpm dev` sobe limpo, `GET /` retorna 200.
- `.env` existe mas com valores VAZIOS — banco de verdade só no cap. 6.

## Observação de navegação no código
- `GET /login` retorna 404 — esperado nesta fase (página será criada no cap. 4+).
- `app/query/route.ts` está comentado de propósito (é um teste do cap. 7).
