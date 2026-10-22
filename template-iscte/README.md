# Modelo de relatório Iscte-IUL

## Novo relatório

1. Copiar a pasta `template-iscte/` inteira e mudar-lhe o nome.
2. Editar `config/info.tex` (título, UC, autores, docente, datas).
3. Pôr o logótipo em `imagens/logo-iscte.png` (enquanto não existir, a capa mostra uma caixa a indicar).
4. Escrever em `capitulos/`, `anexos/`, `referencias.bib` e `config/acronimos.tex`.
5. Compilar `main.tex` (no VS Code: guardar qualquer ficheiro — os outros apontam para o `main.tex`).

## Estrutura

```
main.tex              ordem dos capítulos e anexos
config/info.tex       dados da capa            <- muda sempre
config/acronimos.tex  \newacronym{...}
config/pacotes.tex    pacotes
config/estilo.tex     cores, títulos, cabeçalhos, código, numeração
pretextual/           capa, resumo, abstract   (páginas i, ii, iii, ...)
capitulos/            01-introducao, 02-..., 03-conclusao  (1, 2, 3, ...)
anexos/               \anexo{Título}           (A-1, A-2, B-1, ...)
imagens/              \includegraphics{nome}   (sem pasta nem extensão)
referencias.bib       \cite{chave}
```

Para acrescentar um capítulo: criar `capitulos/04-nome.tex` com `% !TEX root = ../main.tex` na 1.ª linha e um `\input{capitulos/04-nome}` no `main.tex`.

## Atalhos

| O quê | Como |
|---|---|
| Referência a figura/tabela/capítulo | `\cref{fig:x}` → "figura 2.1" (`\Cref` no início da frase) |
| Acrónimo | `\gls{bgp}` |
| Citação | `\cite{rfc4271}` |
| Anexar PDF | `\includepdf[pages=-]{anexos/enunciado.pdf}` |
| Letra sem serifa | descomentar `carlito` em `config/pacotes.tex` |
| Estilo APA | `style=apa` em `config/pacotes.tex` |

Compilação: `latexmk -pdf main.tex` (corre o biber automaticamente). Acrónimos não precisam de `makeglossaries`.
