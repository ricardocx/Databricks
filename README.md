# PUC-RIO | MBA Ciência de Dados e Analytics
## Disciplina: Engenharia de Dados
## Atividade: MVP
## Aluno: Ricardo Cortez
Esse repositório contém os arquivos do Projeto MVP da disciplina. 

### 1. Objetivo
* **Descrição:**
O projeto consiste em analisar os dados de pagamento do **Benefício de Prestação Continuada - BPC*** por município** pagador, sendo os dados disponibilizados de Janeiro a Outubro de 2025.

* **Informações:**

  *O **Benefício de Prestação Continuada- BPC** da Lei Orgânica da Assistência Social- LOAS (BPC) é a garantia de um salário mínimo mensal ao idoso acima de 65 anos ou à pessoa com deficiência de qualquer idade com impedimentos de natureza física, mental, intelectual ou sensorial de longo prazo (aquele que produza efeitos pelo prazo mínimo de 2 (dois) anos), que o impossibilite de participar de forma plena e efetiva na sociedade, em igualdade de condições com as demais pessoas.  
Retirado de [Dabos Abertos - BPC por município pagador](https://dados.gov.br/dados/conjuntos-dados/bpc-por-municipio-pagador).

  **Os municípios analisados são os **Municípios da Faixa de Fronteira e Cidades Gêmeas**.  

  a) Por **Faixa de Fronteira** entende-se **“a faixa de até cento e cinquenta quilômetros de largura, ao longo das fronteiras terrestres”**, conforme a Constituição Federal, artigo 20 – parágrafo 2º. Com base nesta definição, que recepciona os parâmetros da Lei N° 6.634, de 02/05/1979, o IBGE, para fins geocientíficos e estatísticos, identifica e representa os **588 municípios brasileiros com área total ou parcialmente localizada na Faixa de Fronteira distribuídos em 11 estados**, que é a faixa interna de 150 km de largura, paralela à linha divisória terrestre do território nacional.  
A região é composta por 588 municípios, distribuídos da seguinte forma:

  | Região             | Quantidade Municípios                      |
  |--------------------|--------------------------------------------|
  | Amapá              | 08                                         |
  | Acre               | 22                                         |
  | Amazonas           | 19                                         |
  | Mato Grosso do Sul | 45                                         |
  | Mato Grosso        | 28                                         |
  | Pará               | 05                                         |
  | Paraná             | 139                                        |
  | Rondônia           | 28                                         |
  | Roraima            | 15                                         |
  | Rio Grande do Sul  | 196 + Lagoa Mirim + Lagoa dos Patos        |
  | Santa Catarina     | 83                                         |
  | **TOTAL**          | **590**                                    |
  
  Retirado de [ibge.gov.br](https://www.ibge.gov.br/geociencias/organizacao-do-territorio/estrutura-territorial/24073-municipios-da-faixa-de-fronteira.ht-ml?=&t=o-que-e).
  
  b) O IBGE também destaca nesse conjunto, a relação de 33 **cidades gêmeas** nacionais, segundo o Art. 1 da Portaria nº 2.507, de 05/10/2021 do Ministério do Desenvolvimento Regional/Gabinete do Ministro:  
“Art. 1º Serão considerados cidades gêmeas os Municípios cortados pela linha de fronteira, seja essa seca ou fluvial, articulada ou não por obra de infraestrutura, que apresentem grande potencial de integração econômica e cultural, podendo ou não apresentar uma conurbação ou semi-conurbação com uma localidade do país vizinho, assim como manifestações ”condensadas” dos problemas característicos da fronteira, que aí adquirem maior densidade, com efeitos diretos sobre o desenvolvimento regional e a cidadania.”  
Ou seja, aquelas que ficam uma ao lado da outra, mas em países diferentes que exigem aplicação de políticas públicas específicas para atender o grande potencial de integração econômica e cultural, bem como enfrentar os problemas específicos de cidades fronteiriças.  
A tabela 1 lista a relação de municípios:

  | NM_REGIAO     | CD_UF | NM_UF              | SIGLA | CD_MUN  | NM_MUN                  |
  |---------------|-------|--------------------|-------|---------|-------------------------|
  | Norte         | 11    | Rondônia           | RO    | 1100106 | Guajará-Mirim           |
  | Norte         | 12    | Acre               | AC    | 1200054 | Assis Brasil            |
  | Norte         | 12    | Acre               | AC    | 1200104 | Brasiléia               |
  | Norte         | 12    | Acre               | AC    | 1200252 | Epitaciolândia          |
  | Norte         | 12    | Acre               | AC    | 1200435 | Santa Rosa do Purus     |
  | Norte         | 13    | Amazonas           | AM    | 1304062 | Tabatinga               |
  | Norte         | 14    | Roraima            | RR    | 1400159 | Bonfim                  |
  | Norte         | 14    | Roraima            | RR    | 1400456 | Pacaraima               |
  | Norte         | 16    | Amapá              | AP    | 1600501 | Oiapoque                |
  | Sul           | 41    | Paraná             | PR    | 4102604 | Barracão                |
  | Sul           | 41    | Paraná             | PR    | 4108304 | Foz do Iguaçu           |
  | Sul           | 41    | Paraná             | PR    | 4108809 | Guaíra                  |
  | Sul           | 41    | Paraná             | PR    | 4124400 | Santo Antônio do Sudoeste|
  | Sul           | 42    | Santa Catarina     | SC    | 4205001 | Dionísio Cerqueira      |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4300034 | Aceguá                  |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4301875 | Barra do Quaraí         |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4305439 | Chuí                    |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4310603 | Itaqui                  |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4311007 | Jaguarão                |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4315057 | Porto Mauá              |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4315107 | Porto Xavier            |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4315305 | Quaraí                  |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4317103 | Sant'Ana do Livramento  |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4318002 | São Borja               |
  | Sul           | 43    | Rio Grande do Sul  | RS    | 4322400 | Uruguaiana              |
  | Centro-oeste  | 50    | Mato Grosso do Sul | MS    | 5002100 | Bela Vista              |
  | Centro-oeste  | 50    | Mato Grosso do Sul | MS    | 5003157 | Coronel Sapucaia        |
  | Centro-oeste  | 50    | Mato Grosso do Sul | MS    | 5003207 | Corumbá                 |
  | Centro-oeste  | 50    | Mato Grosso do Sul | MS    | 5005681 | Mundo Novo              |
  | Centro-oeste  | 50    | Mato Grosso do Sul | MS    | 5006358 | Paranhos                |
  | Centro-oeste  | 50    | Mato Grosso do Sul | MS    | 5006606 | Ponta Porã              |
  | Centro-oeste  | 50    | Mato Grosso do Sul | MS    | 5006903 | Porto Murtinho          |
  | Centro-oeste  | 51    | Mato Groso         | MT    | 5102504 | Cáceres                 |

  Tabela 1 – Cidades Gêmeas conforme a Portaria Nº 2.507, de 05/10/2021  
  Retirado de [ibge.gov.br](https://www.ibge.gov.br/geociencias/organizacao-do-territorio/estrutura-territorial/24073-municipios-da-faixa-de-fronteira.ht-ml?=&t=o-que-e).

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
| **`NM_MUN`** | Nome do Município | Texto (String) |
| **`CD_RGI`** | Código da Região Imediata (Antiga Microrregião) | Número Inteiro (Integer) |
| **`NM_RGI`** | Nome da Região Imediata | Texto (String) |
| **`CD_RGINT`** | Código da Região Intermediária (Antiga Mesorregião) | Número Inteiro (Integer) |
| **`NM_RGINT`** | Nome da Região Intermediária | Texto (String) |
| **`CD_UF`** | Código da Unidade da Federação (Estado) | Número Inteiro (Integer) |
| **`NM_UF`** | Nome da Unidade da Federação (Estado) | Texto (String) |
| **`SIGLA_UF`** | Sigla da Unidade da Federação (Estado) | Texto (String) |
| **`CD_REGIAO`** | Código da Região (Grande Região) | Número Inteiro (Integer) |
| **`NM_REGIAO`** | Nome da Região (Grande Região) | Texto (String) |
| **`SIGLA_RG`** | Sigla da Região | Texto (String) |
| **`AREA_TOT`** | Área Total do Município em km² | Decimal (Float) |
| **`TOCA_LIM`** | Indica se o limite municipal toca o limite internacional. | Binário (Booleano/NÃO ou SIM) |
| **`AREA_INT`** | Área em km² do município que se encontra dentro da Faixa de Fronteira. | Decimal (Float) |
| **`PORC_INT`** | Porcentagem da área municipal que se encontra dentro da Faixa de Fronteira. | Decimal (Float) |
| **`FAIXA_SEDE`** | Indica se a sede municipal se encontra dentro da Faixa de Fronteira. | Binário (Booleano/Não ou Sim) |
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
