# Pix na Prática com IA

**Do Banco Central à apresentação com Claude, Gemini e Gamma**

Material da aula que mostra como transformar os dados abertos do Pix do Banco Central em gráficos, mapa e slides, com cada IA no papel em que ela é melhor:

| Etapa | Ferramenta | O que faz |
|---|---|---|
| 1. Dados | Banco Central | Fornece o JSON com as transações Pix por município |
| 2. Tratamento | Claude + Power Query | Escreve o código M que limpa e organiza a base |
| 3. Visuais | Excel + Gemini | Tabela dinâmica por estado; o Gemini cria 4 gráficos e 1 mapa |
| 4. Roteiro | Claude | Escreve o prompt da apresentação com os números reais |
| 5. Slides | Gamma | Monta a apresentação final |

## Estrutura do repositório

| Pasta | Conteúdo |
|---|---|
| `dados/` | JSON original da API do Banco Central (jan/2025 a nov/2026, Brasil inteiro, 128.141 registros), compactado em .zip porque tem 55 MB. Descompacte para usar. |
| `power-query/` | Código M do tratamento, pronto para colar no Editor Avançado |
| `prompts/` | Manual de Prompts (Word e PDF) e o prompt do Gemini com os dados por estado já preenchidos |
| `slides/` | Slides da aula (.pptx) |

## Fonte dos dados

- **Banco Central do Brasil**, Pix Dados Abertos, API v1 (Olinda), recurso `TransacoesPixPorMunicipio`
- Mapa dos estados: **IBGE**, API de malhas territoriais

### Colunas usadas na análise

| Coluna | Significado |
|---|---|
| `Ano`, `Mês`, `Nome do Mês` | Criadas a partir de `AnoMes` (ex.: 202607 → 2026, 7, Julho) |
| `Municipio`, `Estado` | Localização do pagador ou recebedor |
| `VL_PagadorPF` | Valor (R$) enviado via Pix por pessoas físicas |
| `VL_RecebedorPF` | Valor (R$) recebido via Pix por pessoas físicas |

## Cuidados com os dados

- **Mês incompleto:** novembro de 2026 ainda estava em andamento na data da coleta.
- **Comparação entre anos:** 2025 tem 12 meses e 2026 vai só até novembro. Para o crescimento anual (YoY), compare os mesmos meses (janeiro a outubro) nos dois anos.
- **Bilhões sem perder precisão:** os valores ficam em reais no Power Query. Os bilhões aparecem só pelo formato da célula no Excel.
- **Registros "NAO INFORMADO":** são transações sem estado identificado e ficam fora dos gráficos por estado.

## Como reproduzir

1. Descompacte o arquivo da pasta `dados/`.
2. No Excel: Dados › Obter Dados › De Arquivo › De JSON. Abra o Editor Avançado e cole o código da pasta `power-query/`, trocando o caminho do arquivo.
3. Monte a tabela dinâmica por estado e siga o **Manual de Prompts**, na pasta `prompts/`.

## Autor

**George Lucas Máximo Ferreira**, economista, cientista de dados e educador. Proativa Educação Corporativa.
Currículo Lattes: http://lattes.cnpq.br/7384837321788311

## Licença

Material didático sob a licença [Creative Commons Atribuição 4.0 Internacional (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.pt-br): você pode usar e adaptar este material, desde que cite o autor.
