# Plano do projeto: gestor e analisador de Google Ads + Instagram/Meta Ads

## Objetivo
1. **Analisar** campanhas (Google Ads e Meta/Instagram): gasto, alcance, conversão, custo por lead, frequência, desempenho por criativo e por público.
2. **Direcionar criativos** para os públicos certos: cruzar criativo × público × resultado e indicar onde cada peça rende mais.
3. **Criar campanhas** para maximizar alcance — sempre como **proposta** aprovada pelo usuário antes de qualquer escrita (regra do CLAUDE.md).

## Fases
| Fase | Entrega | Escrita na conta? |
|---|---|---|
| 1. Leitura | Conectores Meta (MCP `Meta_Campanhas`) e Google Ads (MCP oficial, só leitura). Relatório dos últimos 30 dias por campanha. | Não |
| 2. Análise | Ranking de criativos e públicos, detecção de fadiga (frequência alta, CTR caindo), anomalias, benchmarks. | Não |
| 3. Recomendação | Sugestões de público, orçamento, lance e criativos novos, com justificativa e dados. | Não (só proposta) |
| 4. Escrita com aprovação | Proposta em arquivo → usuário aprova → agente cria campanha/conjunto/anúncio (começa **pausado**). | Sim, só após aprovação explícita |

## Estrutura
```
src/agente/meta/       leitura de Meta Ads (insights, criativos, públicos)
src/agente/google/     leitura de Google Ads (GAQL)
src/agente/analise/    métricas, ranking de criativos × públicos, fadiga
src/agente/propostas/  geração de propostas (JSON/MD) aguardando aprovação
config/                IDs de contas (sem segredos)
relatorios/            relatórios gerados
docs/                  documentação
```

## Fluxo de aprovação (fase 4)
1. Agente grava `propostas/AAAA-MM-DD-nome.md` com: objetivo, público, orçamento, criativos, métrica-alvo, risco.
2. Usuário revisa e responde "aprovo".
3. Só então a escrita é executada, com status **pausado**, e o log do que foi feito é salvo.

## Segmentação de criativos (ideia central)
- Para cada anúncio: coletar resultado por público/idade/gênero/posicionamento/região.
- Calcular custo por resultado e CTR por segmento; marcar segmentos com amostra suficiente.
- Recomendar: "criativo A → público X" quando custo por lead < média da conta com significância mínima.
- Testes A/B de criativo propostos via experimentos do Meta.

## Pendências (precisam do usuário)
- ID da conta de anúncios Meta e da página/conta Instagram.
- Google Ads: projeto Google Cloud, credencial OAuth/ADC, ID da conta (e MCC).
- Meta de negócio: objetivo principal (leads, PTAM vendido, alcance) e custo por lead aceitável.
- Linguagem do código: sugerido Python (já usado no MCP do Google Ads).
