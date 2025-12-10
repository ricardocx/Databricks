# PUC-RIO - MBA Ciência de Dados e Analytics
## Disciplina: Engenharia de Dados
## Aluno: Ricardo Cortez
Esse repositório contém os arquivos do Projeto MVP da disciplina. 

### 1. Objetivo
* **Descrição:**
O projeto consiste em analisar os dados de pagamento do **Benefício de Prestação Continuada - BPC** por município pagador, sendo os dados disponibilizados de Janeiro a Outubro de 2025.

* **Informação:**
O **Benefício de Prestação Continuada- BPC** da Lei Orgânica da Assistência Social- LOAS (BPC) é a garantia de um salário mínimo mensal ao idoso acima de 65 anos ou à pessoa com deficiência de qualquer idade com impedimentos de natureza física, mental, intelectual ou sensorial de longo prazo (aquele que produza efeitos pelo prazo mínimo de 2 (dois) anos), que o impossibilite de participar de forma plena e efetiva na sociedade, em igualdade de condições com as demais pessoas.  
Retirado de [Dabos Abertos - BPC por município pagador](https://dados.gov.br/dados/conjuntos-dados/bpc-por-municipio-pagador).

* **Perguntas a serem respondidas:**
1. Quais os cinco munícipios com o maior valor total pago pelo BPC?
2. Quais as cinco unidades da federação com o maior valor total pago pelo BPC?
3. Qual a lista decrescente por região do Brasil de valor total pago pelo BPC?
4. Qual o valor total pago pelo BPC?
5. Há algum município que não ocorreu pagamento mensal pelo BPC?

### 2. Conjunto de dados
* O arquivo *Beneficiarios_BPC-2025.csv* pode ser baixado do site [gov.br](https://aplicacoes.mds.gov.br/sagi/servicos/misocial?fq=anomes_s:2025*&fq=tipo_s:mes_mu&wt=csv&q=*&rows=100000000&sort=anomes_s%20desc,%20codigo_ibge%20asc&fl=ibge:codigo_ibge,anomes:anomes_s,bpc_ben:bpc_ben_i,bpc_pcd_ben:bpc_pcd_ben_i,bpc_idoso_ben:bpc_idoso_ben_i,bpc_pcd_val:bpc_pcd_val_s,bpc_idoso_val:bpc_idoso_val_s,bpc_val:bpc_val_s&fq=bpc_pcd_ben_i%3A*)

| Coluna | Descrição | Formato/Tipo |
| :--- | :--- | :--- |
| **`ibge`** | Código IBGE do município ao qual o dado se refere. | Número Inteiro (Integer) |
| **`anomes`** | Ano e mês de referência do dado. | Texto/Data (YYYYMM) |
| **`bpc_ben`** | Quantidade **total** de beneficiários do BPC. | Número Inteiro (Integer) |
| **`bpc_pcd_ben`** | Quantidade de beneficiários do BPC na categoria **Pessoa com Deficiência (PcD)**. | Número Inteiro (Integer) |
| **`bpc_idoso_ben`** | Quantidade de beneficiários do BPC na categoria **Idoso**. | Número Inteiro (Integer) |
| **`bpc_pcd_val`** | **Valor total** pago para beneficiários PcD do BPC no período. | Decimal/Moeda (Float/Numeric) |
| **`bpc_idoso_val`** | **Valor total** pago para beneficiários Idosos do BPC no período. | Decimal/Moeda (Float/Numeric) |
| **`bpc_val`** | **Valor total** pago de BPC para todas as categorias. | Decimal/Moeda (Float/Numeric) |

* O arquivo *Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls* pode ser baixado do site [ibge.gov.br](https://geoftp.ibge.gov.br/organizacao_do_territorio/estrutura_territorial/municipios_da_faixa_de_fronteira/2024/Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls)

| Coluna | Descrição | Formato/Tipo |
| :--- | :--- | :--- |
| **`CD_MUN`** | Código do Município (IBGE) | Número Inteiro (Integer) |
| **`CD_REGIAO`** | Código da Região (Grande Região) | Número Inteiro (Integer) |
| **`CD_UF`** | Código da Unidade da Federação (Estado) | Número Inteiro (Integer) |
| **`CD_RGI`** | Código da Região Imediata (Antiga Microrregião) | Número Inteiro (Integer) |
| **`CD_RGINT`** | Código da Região Intermediária (Antiga Mesorregião) | Número Inteiro (Integer) |
| **`NM_MUN`** | Nome do Município | Texto (String) |
| **`NM_RG`** | Nome da Região (Grande Região) | Texto (String) |
| **`SIGLA_RG`** | Sigla da Região | Texto (String) |
| **`NM_RGI`** | Nome da Região Imediata | Texto (String) |
| **`NM_RGINT`** | Nome da Região Intermediária | Texto (String) |
| **`NM_UF`** | Nome da Unidade da Federação (Estado) | Texto (String) |
| **`SIGLA_UF`** | Sigla da Unidade da Federação (Estado) | Texto (String) |
| **`AREA_TOT`** | Área Total do Município em km² | Decimal (Float) |
| **`TOCA_LIM`** | Indica se o limite municipal toca o limite internacional. | Binário (Booleano/0 ou 1) |
| **`AREA_INT`** | Área em km² do município que se encontra dentro da Faixa de Fronteira. | Decimal (Float) |
| **`PORC_INT`** | Porcentagem da área municipal que se encontra dentro da Faixa de Fronteira. | Decimal (Float) |
| **`FAIXA_SEDE`** | Indica se a sede municipal se encontra dentro da Faixa de Fronteira. | Binário (Booleano/0 ou 1) |
| **`CID_GEMEA`** | Indica se a sede municipal é uma Cidade Gêmea. Caso preenchido, sim. | Binário (Booleano/Sim ou Vazio) |

### 3. Modelagem dos dados
* Utilizou-se o Esquema em Estrela com tabelas fato e dimensões.
[Compreendendo o esquema em estrela](https://www.databricks.com/br/glossary/star-schema)

### 4. Carga dos dados
* Utilizou-se a arquitetura medalhão.
[O que é uma arquitetura medallion?](https://www.databricks.com/br/glossary/medallion-architecture)

### 5. Análise dos dados
* a. Qualidade dos dados

Identificou-se algumas colunas com valores nulos, porém, isso não é um problema para a análise a ser realizada.
| Coluna | Motivação para valor **`nulo`** | Fonte |
| :--- | :--- | :--- |
| **`bpc_pcd_val`** | Não houve pago para beneficiários PcD do BPC no período. | *Beneficiarios_BPC-2025.csv* |
| **`bpc_idoso_val`** | Não houve pago para beneficiários Idosos do BPC no período. | *Beneficiarios_BPC-2025.csv* |
| **`CD_RGI`** | campo não será utilizado na análise | *Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls* |
| **`NM_RGI`** | campo não será utilizado na análise | *Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls* |
| **`CD_RGINT`** | campo não será utilizado na análise | *Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls* |
| **`NM_RGINT`** | campo não será utilizado na análise | *Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls* |
| **`FAIXA_SEDE`** | campo não será utilizado na análise | *Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls* |
| **`CID_GEMEA`** | campo não será utilizado na análise | *Mun_Faixa_de_Fronteira_Cidades_Gemeas_2024.xls* |

* b. Respondendo as perguntas citadas na seção **Objetivo**
1. Quais os cinco munícipios com o maior valor total pago pelo BPC?
2. Quais as cinco unidades da federação com o maior valor total pago pelo BPC?
3. Qual a lista decrescente por região do Brasil de valor total pago pelo BPC?
4. Qual o valor total pago pelo BPC?
5. Há algum município que não ocorreu pagamento mensal pelo BPC?

### 6. Autoavaliação
* Durante o projeto 
