# Fundamentos da Engenharia de Dados

## Capítulo I

### O que é Engenharia de Dados? 
Engenharia de Dados é um conjunto de técnicas e procedimentos para tornar os dados disponíveis para uso em um formato utilizável.
Tarefa complexa de tornar os dados brutos utilizáveis para Cientista de Dados e grupos dentro de uma organização. 
A Engenharia de Dados ajuda a tornar os dados mais úteis e acessíveis para os consumidores de dados.
Processo usado para coletar e validar dados de qualidade que possam ser usados por Analistas e Cientistas de Dados.

### A importância dentro da Ciência de Dados
Cultura data-driven: decisões baseadas em dados.

### Hierarquia de necessidades
(Engenharia de dados ->(Instrumentalização -> infraestrutura -> tratamento de dados) -> (analises -> testagens -> aprendizado) -> IA, ML) -> Ciência de Dados

#### O arquiteto projeto, o engenheiro executa.

## Capítulo II
### O que é um pipeline de dados?
É um meio de mover dados de um local para um destino. Ao longo do caminho, os dados são transformados e otimizados, chegando a um estado em que podem ser analisados e usados para desenvolver conhecimento.
O tratamento envolve agregação, organização e movimentação através de uma área temporária (Staging Area).
Construir e manter pipelines de dados é uma das principais atribuições de Enegenheiro de Dados.

### Componentes de um pipeline de dados
1. Origem: captura,inteligação, busca,
2. Processamento: limpeza, tratamento, enriquecimento
3. Destino: data lake, warehouse, tempo real

### Pipeline de dados x Pipeline ETL
ETL : Extraction, transform, load porém é geralmente um subprocesso de um pipeline de dados quando o destino era um data warehouse. Hoje tem inumeras fontes, tipos de processamento e destinos. Há outros processos no pipeline de dados como limpeza, transformação, enriquecimento, segurança, orquestração integração/entrega contínua (CI/CD).

### As principais características ao considerar um pipeline de dados incluem:
• Processamento de dados contínuo e extensível.
• A elasticidade e agilidade da nuvem.
• Recursos isolados e independentes para processamento de dados.
• Acesso democratizado a dados e gerenciamento de autoatendimento.
• Alta disponibilidade e recuperação de desastres

### Principais ferramentas para construir Pipelines de dados
transforção de dados: Apache Beam Model, Airbyte, Stitch, Keebola, dremio (execução de pipeline), fivetran, dataform,  apache airflow (python), apache kafka (tempo real), Apache Spark (Python, Scala, Java, larga escala, distribuido), dbt, aws glue, amazon athena (SQL);
Armazenamento e Cloud: databricks (lakehouse), delta lake, apache hadoop, apache hive, snowflake, bigquery (sql - google), amazon s3, amazon redshift, azure data factory.
real-time analytics: tableau, amazon kinesis, metabase, looker studio, apache flink (logs), druid, superset (exploração e visualização).

### O processo de Engenharia de dados - Data science framework
Entendimento do negócio, compreensão dos dados, preparação dos dados, modelagem, avaliação, criação de pacotes. Ao longo de todo o processo, a execução do pipeline requer monitoramento, segurança, validação e documentção. 

### Ciclo de vida da Engenharia de Dados
Fonte de dados (Batch e Streaming) ->
(Ingestão de Dados: retirar o dado da origem e trazer para o seu ambiente de dados (Airbyte);
Transformação e Enriquecimento: colocar os dados em contexto, combinação de dados de outras fontes e origens;
Carga e Uso dos Dados: armazenar ou usar dos dados para abordagem desejada) (armazenamento ao longo desse processo) ->
Analytics, Machine Learning e IA, Relatórios e Dashboards
Tarefas complementares:
- Arquitetura de Dados: seja na estrutura ou na infraestrutura;
- Gestão de dados e metadados: processos burocráticos, LGPD, dados sensíveis, 
- Orquestração: concateção dos pipeline, ligamento para todas as tecnologias de diferentes pipelines utilizados em diferentes etapas do ciclo de vida (Apache flow);
- Segurança: quem tem acesso ao que, dados brutos, dados sensíveis, é cloud?, tem vpc? alta disponibilidade, escalabilidade, criptografia;
- CI/CD (integração contínua e entrega contínua) é uma abordagem de desenvolvimento de software em que todos os desenvolvedores trabalham juntos em um repositório compartilhado de código e, à medida que as alterações são feitas, há um processo de build a automatizado para detectar problemas de código;
- DataOps: O DataOps é um sistema de entrega de resultados que é baseado na junção e na análise de dados. O seu foco está em se tornar uma metodologia de trabalho interfuncional e que deve atuar em todas as etapas do desenvolvimento do produto. Assim, é possível garantir alta qualidade para o produto do projeto.
