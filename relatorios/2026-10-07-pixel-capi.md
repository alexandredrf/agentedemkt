# Pixel e API de Conversões: dataset "Valor 360" (1201404035263201)
Janela: 2026-09-09 a 2026-10-06 (máximo de 28 dias retidos pelo Meta).

## Saúde
- Ativo. Último disparo: browser 2026-10-06 18:06 e servidor 18:08 (horário do Pacífico).
- Eventos por origem (28 dias): servidor 3.636, browser 3.254. A API de Conversões está enviando junto com o pixel.
- O dataset "Pixel page Arthur" (3349001225301746) nunca disparou: ignorar.

## Volume por evento (28 dias, contagem bruta; pode somar browser + servidor)
- PageView: milhares (dezenas por hora nos picos).
- InitiateCheckout: ~115.
- Purchase: 8 (em 30/09, 02/10, 03/10, 05/10 e 06/10). Se a contagem soma browser + servidor, são ~4 compras reais.
- AddToCart: 2 (só em 05/10).
- Sem volume de cadastro (CompleteRegistration/Lead). "SubscribedButtonClick" aparece na qualidade, mas sem eventos na janela.

## Qualidade de correspondência (EMQ, escala de 10)
| Evento | EMQ | Chaves a 100% | Lacunas |
|---|---|---|---|
| SubscribedButtonClick | 7,7 | e-mail, IP, user agent, fbp | - |
| Purchase | 6,2 | e-mail, IP, user agent, fbp, external_id | telefone, nome, fbc |
| InitiateCheckout | 6,1 | IP, user agent, fbp | e-mail ausente |
| PageView | 6,1 | IP, user agent, fbp | e-mail 4,5%, fbc 21,5% |

## Conclusões
1. Rastreamento funciona, mas o volume de compra é baixo demais para otimizar campanha por Purchase (o Meta pede ~50 conversões/semana). Compra ocorre hoje sobretudo fora dos anúncios.
2. Não existe evento de cadastro: o objetivo "criar-conta" não pode ser otimizado nem medido.
3. fbc em só 21,5% dos PageView: parte dos cliques de anúncio chega sem identificação (o parâmetro fbclid pode estar sendo perdido).
4. Melhorias de EMQ: enviar telefone e nome em Purchase; e-mail em InitiateCheckout.
