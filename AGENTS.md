# Regras do projeto — Acme Dashboard

## Contexto
Projeto de estudos do curso [Next.js Learn — App Router](https://nextjs.org/learn/dashboard-app).
O usuário estuda capítulo por capítulo; o agente atua como **guia**:
explica, revisa o código e só avança de capítulo com confirmação do usuário.
Nunca implemente capítulos futuros por conta própria.

## Idioma
Responda sempre em português (pt-BR). Mensagens de erro do código também em pt-BR.

## Regra do README (obrigatória)
O `README.md` é o diário do curso. A cada capítulo concluído:
1. Marque o checkbox do capítulo na seção "Progresso no curso".
2. Atualize as seções afetadas (stack, como rodar, estrutura, notas técnicas).
3. Faça um commit dedicado por capítulo, ex.:
   `feat(cap-4): paginas e layouts do dashboard`.

## Padrão de commits
- Um commit por unidade de trabalho, mensagens convencionais em pt-BR
  (`chore:`, `feat(cap-N):`, `fix:`).
- Antes de commitar: `pnpm exec tsc --noEmit` deve passar zerado.
- Nunca commitar segredos: `.env` está no `.gitignore`; só `.env.example`.

## Padrões de código
- Acesso ao Postgres sempre lazy via `getSql()` (`app/lib/data.ts`,
  `app/seed/route.ts`) — o dev precisa subir mesmo sem `POSTGRES_URL`.
- `GET /login` em 404 é esperado até o capítulo 4; não "corrija" criando a
  página antes da hora.
- `app/query/route.ts` comentado é proposital (exercício do cap. 7).

## Ambiente
- Comandos sempre dentro de `nextjs-dashboard/`: `pnpm dev`, `pnpm install`.
- Não mover o projeto de pasta sem pedir confirmação explícita.
- Arquivos `CONTEXTO-PROJETO.md` e `AGENTS.md` são metadocumentação do
  projeto: mantenha-os atualizados, mas não os trate como código do curso.
