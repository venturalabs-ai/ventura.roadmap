# Skill: ventura.roadmap — LOOP Skill Engine / Deterministic Replay

![MIT](https://img.shields.io/github/license/chamseddinehiddoud/ventura.roadmap)
![stars](https://img.shields.io/github/stars/chamseddinehiddoud/ventura.roadmap)
![forks](https://img.shields.io/github/forks/chamseddinehiddoud/ventura.roadmap)

Skill de planejamento e execução de carreira técnica com **execução
determinística**: explore uma vez, compile o roadmap, replique com ~zero
tokens, regenere quando o mercado (ou o objetivo) mudar.

## Trigger

Use quando o usuário quiser: planejar carreira técnica, saber "o que estudar
para virar X", montar roadmap de aprendizado, revisar progresso, mudar de
área na tecnologia.

## Arquitetura Token-Efficient & Regenerative

| Fase | Descrição | Consumo |
|---|---|---|
| **Explore** | Modelo forte analisa perfil + área + objetivo (uma vez) | Alto (único) |
| **Compile** | Gera roadmap em `plano.md` (fases, passos, critérios) | Baixo |
| **Replay** | "Próximo passo" do dia — sem redecidir a trilha | Mínimo/Zero |
| **Regenerate** | Área/mercado mudou → regenere o plano | Sob demanda |

## Receita determinística (Replay)

```text
1. PEDIDO   — "próximo passo" | "o que estudar hoje" | "revisar fase"
2. RECEITA  — consulta plano.md: fase atual, passo N, recurso, critério
3. EXECUTA  — 1 tarefa prática + 1 recurso curado + 1 critério de avanço
4. REGISTRA — progresso: passo concluído, dificuldade, data
5. STOP-YIELD — sem avanço real (bloqueio/desânimo) → propõe ajuste
```

## Regras de engenharia

- **Token Budget** — Explore: até 8k tokens. Replay: < 200 tokens.
- **Context Firewall** — o replay só vê o passo atual (nunca o roadmap inteiro).
- **Prefix Caching** — o sistema deste arquivo fica byte-stable.
- **Skill Distillation** — trilha validada vira plano permanente.
- **Regeneração** — nova vaga/área/meta → volta ao Explore com memória.

## Como compilar o roadmap (Explore → Compile)

```text
1. Entrevista rápida: área, nível atual, tempo semanal, objetivo (vaga/skill)
2. Seleciona a área curada e define fases com critérios claros
3. Compila plano.md: 4 fases, passos sequenciais, recursos, critérios
4. Valida com o usuário e ativa o Replay
```

## Exemplo de uso

```text
Atue como ventura.roadmap (modo REPLAY). Meu plano.md diz: "Backend, Fase 2,
Passo 4: modelagem de dados". Liste a tarefa prática, o recurso curado e o
critério de avanço para hoje. Use menos de 200 tokens e registre o progresso.
```
