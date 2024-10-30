# Dashboard Corporativo com Integração MySQL e Azure

Este projeto consiste na criação de um banco de dados, coleta e transformação de dados, e criação de um dashboard corporativo utilizando o Power BI. Abaixo estão os passos realizados para a criação do projeto.

## Descrição do Projeto

- **Objetivo**: Criar um banco de dados (BD), coletar os dados utilizando o Power BI e transformá-los para construção de um relatório corporativo.
- **Integração de Dados**: O banco de dados foi configurado localmente devido à indisponibilidade de créditos no Azure, com dados populados a partir do script `azure_company.sql`.
- **Ferramentas Utilizadas**: MySQL para banco de dados e Power BI para coleta, transformação de dados e criação do relatório.

## Etapas Realizadas

### 1. Estruturação do Banco de Dados

- Criação do BD com tabelas relacionadas, inserção de dados e configuração para integração com Power BI.
- **Script utilizado**: `azure_company.sql`.

### 2. Preparação e Transformação de Dados no Power BI

- **Verificação de Tipos de Dados**: Revisão dos cabeçalhos e ajuste dos tipos de dados sugeridos pelo Power BI, incluindo conversão de valores monetários para o tipo *double preciso*.
- **Tratamento de Valores Nulos**: Remoção de colunas desnecessárias geradas pelo Power BI; como não havia nulos relevantes, a limpeza foi pontual.
- **Divisão de Colunas Complexas**:
  - Coluna `address` da tabela `employee` foi dividida em `number`, `street`, `city` e `state` usando o caractere "-" como delimitador.
  - Realizado ajuste adicional em valores da coluna `street` (substituição de "fire-Oak") para evitar colunas extras.

### 3. Mescla e Junção de Tabelas para Enriquecimento de Dados

- **Integração de Departamentos**:
  - Mescla das tabelas `employee` e `department` para incluir o nome do departamento (`Dname`) aos dados de cada colaborador.
  - Colunas não utilizadas, exceto `Dname` (renomeada para `Department`), foram removidas.

- **Relacionamento de Colaboradores e Gerentes**:
  - Junção entre `employee` e ela mesma para associar colaboradores a seus respectivos gerentes, utilizando as colunas `Super_Ssn` e `Ssn`.

- **Mescla de Colunas Nome e Sobrenome**:
  - Unificação das colunas `FirstName` e `LastName` em uma única coluna `Name` com separador de espaço.

- **Integração de Departamentos e Localizações**:
  - Mescla entre as tabelas `department` e `dept_locations` para consolidar os locais de cada departamento. Colunas desnecessárias e duplicadas foram removidas, e `Dname` foi combinada com `Dlocation` para maior clareza.

### 4. Agrupamento e Análise de Dados

- **Agrupamento por Gerente**:
  - Agrupamento dos colaboradores por gerente para análise do número de colaboradores por gerente.

## Relatório Final

O relatório final foi desenvolvido no Power BI, utilizando as transformações e integrações descritas acima.

Desenvolvido por: **Cibele Gomes Domingos Moraes**
