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

## Capítulo 3
### Como iniciamos um projeto de pipeline de dados?
C) Iniciamos pela compreensão dos requisitos de negócios e o que se espera do uso de dados do dia a dia.
Os pipelines de dados são parte da arquitetura de dados de uma empresa, que por sua vez é parte da plataforma de dados da empresa. Cada pipeline de dados deve ter um propósito.
PoC -> Prova de Conceito: uma espécia de laboratório que simula cenários, valida requisitos de negócio, testa ferramentas e ajuda a prever custos. 

### Pipeline de dados x Pipeline ETL x Pipeline de ML
Pipeline de Machine Learning { BD Transacional -> Pipeline de dados [extração para um data lake -> limpeza e transformação -> data lake: ETL (Extraction, Transform, Load) (Os usuários de negócios podem requerer o acesso aos data lakes através Consultas Ad-Hoc com SQL ou outra conexão.) -> Processamento: machine Learning, deep learning -> fluxo de dados (deploy)]}

### Comece a arquiteteura de pipelines de dados por estas perguntas
- Quais são os requisitos de negócio?
- Quais resultados finais são necessários?
- Os dados estão disponíveis? Quais são as fontes?
- Quais tipos de formatos de dados estão disponíveis?
- Qual o crescimento esperado do volume de dados?
- Quanto de armazenamento será necessário?
- Quanto de capacidade computacional será necessário?
- Usaremos dados em batch, streaming ou ambos?
- Já temos tecnologia que permita criar os pipelines?
- Quais tecnologias devem ser consideradas?
- Quais são os Acordos de Nível de Serviços (SLA's)?
- Qual custo de implementar e manter os pipelines?
- Qual será o destino do pipeline?
- Como será o monitoramento?
- Usaremos diversos pipelines encadeados?
- Vamos criar pipelines locais, na nuvem ou ambos?

### Estudo de Caso 1 - Empresa de área de manufatura
Compreensão do problema: Empresa de manufatura de pequeno porte
Compreensão do que deve ser entregue: extração dos dados
Pesquisando as fontes de dados: máquinas q enviam os resultados em formato de arquivo txt para os servidores
Identificando a infraestrutura atual e o que será necessário: aws

#### esboço do pipeline
Máquina irão enviar os dados para o servidor. Servidor será minha fonte de dados que irei realizar uma extração e aqui começa o meu pipeline. Essa extração da fonte irá subir para um data lake em nuvem como proposta da empresa. Aplicaremos uma limpeza e tratamento e criaremos outro data lake, todos em nuvem. Os dados limpos irão alimentar o sistema de logistica e através do machine learning criaremos uma modelo que irá prever se alguma máquina irá precisar de manutenção preventiva ou não. 

#### batch, streaming ou ambos?
De acordo com o estudo de caso, os dados são produzidos em Batch. As máquinas sempre registram os dados mesmo que não utilizamos ou utilizamos em horários diferentes. Em streaming, se estivessemos coletando dados direto das máquinas em tmepo real. 

#### Volume de dados e armazenamento
Empresa tem 10 máquina, cada qual gerando 1 arquivo de 1 MB a cada 1 hora.
Mais 5 máquinas irão chegar no próximo semestre. Logo esperamos um crescimento de 50% no volume de dados.

#### Repositório de dados
AWS Data Lake, AWS Glue e Amazon Cloud Watch

#### Extração e Processamento dos Dados
Apache Kafka para extrair os dados e enviar para o ambiente em nuvem, onde o Apache Spark poderia fazer o processamento, evitando ter um armazenamento intermediário.
Ao invés de armazenar os dados primeiro no Data Lake e processar depois já processaríamos os dados no momento da extração aplicando as transformações necessários e reduzindo o espaço total de armazenamento de dados.

#### Containers e Orquestração de Containers como Parte da Solução
Precisamos publicar, monitorar e atualizar os modelo de ML.
Publicar os modelos de ML através de containers (máquinas virtuais super leves). O Engenheiro de ML faz o deploy do modelo através de containers. 
Amazon Elastic Container Service (Amazon ECS) na nuvem AWS.
Como gerenciar os containers? Precisamos de uma serviço de orquestração dos containers, sendo o Kubernetes uma opção. E podemos usar o serviço Amazon Elastic Kubernetes service (EKS). Esses 2 serviços necessitam de uma camada computacional e podemos usar uma arquitetura serverless como o AWS Fargate.

#### IaC - Infraestrutura como código e CI/CD
Como gerenciar a criação, atualização e manutenção de toda essa infraestrutura na nuvem?
Aí que entra o conceito de IaC. O objetivo é gerenciar a infraestrutura de forma simples permitindo mudanças rápidas e implementando as boas práticas de CI/CD. Essencialmente estamos implementando DataOps.

#### Custo do Pipeline de Dados
Devemos considerar:
- AWS Data Lake
- Apache Kafka/Apache Spark
- Amazon ECS, EKS e Fargate
- Construção dos modelos de ML
- Automação com IaC e boas práticas CI/CD
- Monitoramento




