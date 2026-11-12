# Analisando o Pix com IA: do dado aberto do Banco Central à interpretação

Material da aula que mostra como usar Inteligência Artificial para transformar dados abertos do Pix em informação: da coleta na API do Banco Central à leitura crítica dos resultados.

O recorte analisado são as **pessoas físicas (PF) do estado de São Paulo**, de janeiro a novembro de 2026.

## O que tem neste repositório

| Pasta | Conteúdo |
|---|---|
| `dados/json/` | Arquivo original baixado da API do Banco Central (61.292 registros), compactado em .zip porque tem 26 MB. Descompacte para usar |
| `dados/xlsx/` | Mesmo conteúdo convertido para Excel com ajuda de IA, sem perda de dados |
| `slides/` | Apresentação da aula (.pptx) |
| `prompts/` | Prompts usados com a IA em cada etapa |

## Fonte dos dados

- **Banco Central do Brasil**, Pix Dados Abertos, API v1 (Olinda)
- Recurso: `TransacoesPixPorMunicipio`
- Endereço: https://olinda.bcb.gov.br/olinda/servico/Pix_DadosAbertos/versao/v1/aplicacao#!/recursos

### Dicionário das colunas

| Coluna | Significado |
|---|---|
| `AnoMes` | Ano e mês de referência (ex.: 202605 = maio/2026) |
| `Municipio_Ibge`, `Municipio` | Código IBGE e nome do município |
| `Estado_Ibge`, `Estado` | Código IBGE e nome do estado |
| `Sigla_Regiao`, `Regiao` | Região do país |
| `VL_PagadorPF` / `QT_PagadorPF` | Valor (R$) e quantidade de Pix **enviados** por pessoas físicas |
| `VL_PagadorPJ` / `QT_PagadorPJ` | Valor (R$) e quantidade de Pix **enviados** por pessoas jurídicas |
| `VL_RecebedorPF` / `QT_RecebedorPF` | Valor (R$) e quantidade de Pix **recebidos** por pessoas físicas |
| `VL_RecebedorPJ` / `QT_RecebedorPJ` | Valor (R$) e quantidade de Pix **recebidos** por pessoas jurídicas |
| `QT_PES_*` | Quantidade de pessoas pagadoras ou recebedoras |

> Observação: 11 registros (um por mês) aparecem como município "N/D" e estado "NAO INFORMADO", sem código IBGE. Eles vêm assim da própria fonte.

## Etapas da aula

1. **Coleta:** download do JSON na API do Banco Central.
2. **IA organiza:** conversão do JSON para Excel, conferida linha a linha contra o original.
3. **Gráficos:** filtro de São Paulo e de pessoas físicas, com valores mensais pagos e recebidos.
4. **Interpretação:** leitura crítica, levantamento de hipóteses e cuidados com os dados.

## Principais achados (São Paulo, PF, jan–out/2026)

- Pessoas físicas **pagaram R$ 2,72 trilhões** e **receberam R$ 2,78 trilhões** via Pix, cerca de 25% do total pago por PFs no Brasil.
- Em **todos os meses** elas receberam mais do que pagaram: são **R$ 55 bilhões** a mais no período.
- Valor médio de **R$ 215 por Pix pago** e **R$ 404 por Pix recebido**.
- Os valores cresceram cerca de **14%** de janeiro a outubro. Fevereiro é o vale do ano, por ser um mês mais curto e com Carnaval.
- **Novembro está incompleto** na data da coleta e não deve ser comparado com os meses fechados.

## Como reproduzir

1. Baixe os dados na API do Banco Central (link acima) ou descompacte o arquivo .zip em `dados/json/`.
2. Use os prompts da pasta `prompts/` em uma ferramenta de IA para converter e analisar os dados.
3. No Excel, filtre `Estado = SÃO PAULO` e some as colunas `VL_PagadorPF` e `VL_RecebedorPF` por `AnoMes`.
4. Compare os seus resultados com os desta aula.

## Autor

**Prof. George**, economista, cientista de dados e educador. Proativa Educação Corporativa.
Currículo Lattes: http://lattes.cnpq.br/7384837321788311

## Licença

Material didático sob a licença [Creative Commons Atribuição 4.0 Internacional (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.pt-br): você pode usar e adaptar este material, desde que cite o autor.
