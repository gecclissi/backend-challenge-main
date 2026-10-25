# Contexto para continuar com o Claude em outro PC

> Cole no novo chat: "Leia CONTEXTO.md e README.md e vamos continuar de onde paramos."

## Quem sou e qual o objetivo
- Tenho conhecimento de programação, mas sou iniciante em nomenclaturas e sistemas distribuídos.
- Este é um **desafio técnico de contratação** (Jungle Gaming) descrito no `README.md`.
- **Prazo: 2 dias.** Quero fazer o máximo possível já no primeiro dia.
- Vou **apresentar e explicar o código passo a passo** numa entrevista, então preciso entender cada decisão.
  Explique tudo de forma didática enquanto construímos.

## O que já foi feito
- Parte 1 concluída: visão geral do projeto, glossário de termos (idempotência, ledger, inbox/outbox,
  locks, SQS, DLQ, DDD etc.) e levantamento de bibliotecas de mercado.
- Nenhum código escrito ainda. A pasta tem só `README.md` e este arquivo.

## Decisões já combinadas (Claude propôs, eu concordei)
- **Entender > completude.** Código simples e defensável vale mais do que muitas features.
- **Prioridade pelos pontos da avaliação:** Money sem `number` → saldo nunca negativo → sem duplicidade
  → ledger → idempotência no banco → cenário 100 → 80 + 80 → API → SQS/inbox → outbox → workers
  → testes de concorrência → observabilidade → `ARCHITECTURE.md`.
- **Cortes:** autenticação fica só documentada (AuthGuard no-op), sem teste de carga e sem partidas dobradas.
- **Escolhas técnicas:** Bun + NestJS + TypeScript estrito, **MikroORM**, **decimal.js** para dinheiro,
  **lock pessimista por wallet** (`SELECT ... FOR UPDATE`), PostgreSQL e **LocalStack** via Docker Compose.
- **Ritmo:** dia 1 com setup, domínio, banco e API; dia 2 com SQS, outbox, workers, testes e documentação.

## Próximos passos
1. Garantir que o PC tenha: **Docker Desktop** (com WSL2 e virtualização ativa na BIOS), **Bun**, **Git**.
   Verificar com `docker info`, `bun --version` e `git --version`.
2. Claude escreve um documento de design curto (o mapa do projeto para a apresentação).
3. Criar o esqueleto do projeto e subir Postgres + LocalStack.
4. Começar pela classe `Money`, com testes.
