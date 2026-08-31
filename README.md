# Financiamento da Inovação — UNEMAT

Site da disciplina **Políticas e incentivos para a inovação e avaliação de impacto**,
módulo 11 da Especialização em Gestão e Inovação em Negócios (GIN), UNEMAT — Campus de Sinop.

Oferta de setembro de 2026. Encontros síncronos por Google Meet nos sábados 12/09 e 26/09,
das 8h às 12h e das 14h às 18h.

Site publicado: <https://daniellindomar.github.io/inovacao/>

## Estrutura

- `index.qmd` — hub de navegação
- `s1-*.qmd`, `s2-*.qmd` — o conteúdo discutido em cada bloco dos encontros síncronos
- `cat-*.qmd` — catálogo de instrumentos de financiamento à inovação
- `lab*.qmd` — laboratórios em R, executados no navegador via [quarto-live](https://r-wasm.github.io/quarto-live/)
- `casos.qmd`, `caso-lei-do-bem.qmd`, `trabalho-final.qmd` — avaliação
- `dados/` — bases usadas nos laboratórios

## Como renderizar localmente

```bash
quarto add r-wasm/quarto-live   # uma vez
quarto preview
```

A publicação é automática: o workflow em `.github/workflows/publicar.yml` renderiza e
publica na branch `gh-pages` a cada push na `main`.

## Identidade visual

`estilo-curso.scss` é compartilhado com o site de [Econometria Interativa](https://daniellindomar.github.io/econometria/),
acrescido do sistema de cores que marca a natureza de cada instrumento
(não reembolsável, fiscal, reembolsável, equity).

---

Prof. Dr. Lindomar Pegorini Daniel · UNEMAT — Campus de Sinop
