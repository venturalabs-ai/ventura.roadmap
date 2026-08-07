# Skill: ventura.roadmap — LOOP Skill Engine / Constrained Replay

![License](https://img.shields.io/github/license/venturalabs-ai/ventura.roadmap)
![Stars](https://img.shields.io/github/stars/venturalabs-ai/ventura.roadmap)

Skill de planejamento e execução de carreira técnica com **replay restrito por plano versionado**: explore quando necessário, compile o roadmap, reutilize decisões registradas e regenere quando mercado, objetivo ou restrições mudarem.

## Trigger

Use quando o usuário quiser planejar carreira técnica, montar roadmap de aprendizado, revisar progresso ou mudar de área.

## Arquitetura de eficiência

| Fase | Descrição | Meta de contexto |
|---|---|---|
| **Explore** | Analisa perfil, área e objetivo | Maior |
| **Compile** | Gera `plano.md` com fases, passos e critérios | Reduzida |
| **Constrained Replay** | Executa o próximo passo usando somente o contexto necessário | Mínima necessária |
| **Regenerate** | Reavalia quando objetivo, mercado ou restrições mudarem | Sob demanda |

O consumo real de tokens depende do modelo, runtime e contexto. Este projeto não afirma execução com zero tokens nem determinismo de saídas LLM.

## Receita de replay

```text
1. PEDIDO   — próximo passo / revisão de fase
2. RECEITA  — consulta plano.md: fase atual, passo, recurso e critério
3. EXECUTA  — tarefa prática + recurso + critério de avanço
4. REGISTRA — progresso, dificuldade e data
5. STOP-YIELD — bloqueio ou ausência de avanço → propõe ajuste
```

## Regras de engenharia

- definir token/context budget mensurável por runtime;
- limitar o replay ao contexto necessário;
- usar prefixos estáveis apenas quando o provedor/runtime suportar cache;
- versionar trilhas e critérios de avanço;
- voltar ao Explore quando objetivo ou restrições mudarem materialmente.

## Compilar o roadmap

```text
1. Defina área, nível atual, tempo disponível e objetivo.
2. Estruture fases com critérios observáveis.
3. Registre plano.md com passos sequenciais e recursos.
4. Revise o plano e inicie o Constrained Replay.
```
