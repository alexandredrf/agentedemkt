# Agente de marketing (gestor de tráfego)

Projeto para gerir a mídia paga da Valor 360: **Instagram/Meta Ads** e **Google Ads**.

## Regras
- Começa **somente leitura**: analisar gasto, conversão e custo por lead. Nada de alterar conta sem aprovação explícita.
- Qualquer escrita (pausar, lance, orçamento, criar anúncio) só como **proposta** que o usuário aprova antes.
- Credenciais ficam fora do repositório (variáveis de ambiente do Windows ou arquivo ignorado pelo git). Nunca commitar.
- Respostas em português.

## Contexto
- Produto: Valor 360 (PTAM online) e o Finder, em Base44 (repositórios `valor360` e `valor360_scrapping`).
- Meta: pixel e API de Conversões já ativos no valor360 (evento de compra).
- Google Ads: o servidor MCP oficial (github.com/googleads/google-ads-mcp) é só leitura. No Windows deste computador o `pipx run` é bloqueado por política de Controle de Aplicativo; funciona chamando o Python de um venv (`python -c "from ads_mcp.server import run_server; run_server()"`).
- Para configurar o Google Ads: projeto no Google Cloud com a Google Ads API ativa, credencial OAuth (app para computador) ou gcloud ADC, ID da conta (e da MCC, se houver).

## Próximos passos
1. Decidir a estrutura (conectar Meta Ads e Google Ads em modo leitura).
2. Primeiro relatório: gasto, conversões e custo por lead por campanha, últimos 30 dias.
3. Só depois, desenhar a camada de escrita com aprovação.
