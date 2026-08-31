# Como estas bases foram geradas

Ambas são **simuladas**. É proposital: com dados simulados o efeito verdadeiro é conhecido,
e o aluno pode verificar se o método de estimação acertou — o que nenhuma avaliação com
dados reais permite. É a mesma lógica das *Aplicações* do site de Econometria.

Semente fixa: `20260912`.

## fomento_sim.csv

Painel de **1.500 empresas** em dois momentos (2022 e 2025), 3.000 linhas.

| Coluna | Conteúdo |
|---|---|
| `empresa` | identificador |
| `ano` | 2022 ou 2025 |
| `pos` | 0 antes, 1 depois |
| `beneficiaria` | 1 se aderiu ao incentivo |
| `setor`, `porte`, `faturamento_mi`, `lucro_real` | características da empresa |
| `pd` | dispêndio anual em P&D, em R$ mil |

**Processo gerador**

- Porte sorteado: 28% micro, 42% pequena, 30% média. Faturamento sorteado dentro da faixa do porte.
- Probabilidade de estar no lucro real: 8% (micro), 30% (pequena), 72% (média).
- `pd` no período anterior: normal com média 420 (micro), 600 (pequena), 880 (média) e desvio 190.
- **Seleção não aleatória** — logit com `score = -3,6 + 2,1·lucro_real + 0,0032·pd_antes + 0,35·(porte = média)`.
  Ou seja: adere quem está no lucro real e quem já gastava mais. É a origem do viés.
- Tendência comum do período: **+180**, aplicada aos dois grupos.
- Choque comum: normal(0, 120).
- **Efeito verdadeiro do tratamento: +150**, aplicado apenas às beneficiárias.

**Valores resultantes** (médias na amostra gerada)

|  | Antes | Depois |
|---|---:|---:|
| Beneficiárias | 791,9 | 1.109,9 |
| Não beneficiárias | 537,3 | 717,3 |

- Viés de seleção (diferença no período anterior): **254,6**
- Comparação bruta (diferença no período final): **392,6**
- Diferenças-em-diferenças: **138,0** — contra um efeito verdadeiro de **150,0**

A diferença entre 138 e 150 é ruído amostral, e é usada no Laboratório 2 para discutir
por que uma estimativa vem com intervalo de confiança.

## projeto_inovacao.csv

Fluxo de caixa de um projeto de inovação de **R$ 500 mil**, em seis anos, valores em R$ mil.

| ano | investimento | custeio | receita incremental | fluxo líquido |
|---:|---:|---:|---:|---:|
| 0 | −500 | 0 | 0 | −500 |
| 1 | 0 | −95 | 75 | −20 |
| 2 | 0 | −110 | 290 | 180 |
| 3 | 0 | −120 | 380 | 260 |
| 4 | 0 | −125 | 425 | 300 |
| 5 | 0 | −130 | 450 | 320 |

- VPL a 12% ao ano: **182,9**
- TIR: **22,1%**

Calibrado para que o projeto seja viável mas não trivialmente lucrativo — o VPL muda de
sinal entre 22% e 26%, o que torna o exercício de sensibilidade à taxa de desconto informativo.
