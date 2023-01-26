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

## Capítulo 4

### Por que o armazenamento de dados é importante?
Porque permite que a empresa extraia valor dos dados.
Onde os dados residem? Os dados residem em arquivos que são armazenados no disco físico ou outras mídias de armazenamento de dados.
Parquet: formato de armazenamento colunar para armazenar grandes qntds de dados de forma eficiente, Hadoop (em ambiente distribuido) permitindo consultas e análises eficientes usando ferramente como Apache Spark. Compartilhamento de dados entre sistemas.
Avro: formato de serialização para armazenar dados; oferece suporte a estruturas de dados complexas; armazenamento de grandes quantidades de dados; dados com estruturas complexas; compartilhamento de dados entre sistemas; processamento com hadoop
ORC: Optmized row columnar é um formato de armazenamento colunar para armazenar grandes quantidades de dados de forma eficiente; compostos de grupos de linha; suportam como datetime, decimal e listas mapas etc
CSV:são simples fáceis e amplamente usados para armazenar dados; sem compressão, sem cabeçalhos, fáceis de usar desde que o volume de dados não seja muito grande. 
JSON: JavaScript Object Notation formato de intercâmbio de dados leve que é fácil para os humanos leres e escreverem e fácil para as máquinas analisares e gerarem. 
HDF5 ou PICKLE?
SQL/NoSQL ou Baseado em Arquivos? 
SQL: é o formato tradicional de armazenamento de dados no formato tabular; é um dos formatos de armazenamento mais antigos e amplamente usado nos dias de hoje; ideal para dados estruturados (tabular); utiliza SGBDs (Sistemas Gerenciadores de Banco de Dados) como Oracle, PostgreSQL, SQL Server ou MySQL; 
NoSQL: nasceu na era do Big Data para permitir o armazenamento de dados em diferentes formatos, em especial, dados semi-estruturados como no formato JSON, SML ou colunar; são sistemas de armazenamento orientador à performance e facilidade de uso; MongoDB, Cassandra, HBase, Redis.
Baseado em arquivos: Parquet, Avro, JSON, CSV, ORC, HDF5, etc. 

### Os padrões de acesso definem o tipo de armazenamento
Quantos sistemas precisarão de acesso à camada de armazenamento de dados?
Com que frequência os sistemas acessarão o armazenamento de dados?
Qual o colume dedados que esses sistemas estarão lendo?
Quanta lógica será aplicada por esses sistemas de dados?
Como o sistema acessa tecnicamente os dados?

### Armazenamento Colunar x Linha
Baseado em linha: fácil e estruturado porém não foca na performance (como uma matriz)
Baseado em coluna: parece uma tupla do python, cria-se um id para a busca focando na performance. no geral os dados nosql seguem essa lógica.

### Quando usar um Data Warehouse?
Um data warehouse é um tipo de banco de dados projetando especificamente para consultas e análises eficientes de grande quantidades de dados. Ele é normalmente usado para armazenar e gerenciar dados de várias fontes, como bancos de dados transacionais ou arquivos de log. Data warehouse é um conceito, logo pode ser criado como SGBD SQL ou NoSQL, no formato colunar ou baseado em linha.
Um data warehouse é uma boa opção se você tiver grande volume de dados que precisa armazenar e analisar com eficiência ou se precisar oferecer suporte a sistemas de relatórios e inteligência de negócios.
DW -> limpa e organiza, depois carrega.

### Quando usar um Data Lake?
Permite o armazenamento dos dados no seu formato bruto para posterior processamento e organização; 
DL -> Carrega, depois limpa e organiza.
DL é um repositório centralizado que permite armazenar e processar grandes quantidades de dados estruturados e não estruturados em escala.
Ele foi projetado para lidar com uma ampla variedade de tipos de dados. Assim como o DW, o Data Lake é um conceito. Por definição não se usa um armazenamento SQL. Necessidade de uma repositório de dados centralizados.
Em geral, um Data Lake é uma boa opção se você tiver grandes volumes de dados estruturados e não estruturados que precisa armazenar e processar em escala ou se precisar de um repositório centralizado para armazenar e processar dados de várias fonte.

### Quando usar um Data Lakehouse
Plataforma de dados moderna construída a partir de uma combinação de um Data Lake e um Data Warehouse. Une o armazenamento flexível de dados não estruturados de um Data Lake e os recursos e ferramentas de gerenciamento de Data Warehouse e os implementa estrategicamente como um sistema maior.
From BI to AI (nem sempre)
Vantagens: escalabilidade, flexibilidade, desempenho de consulta, repositório centralizado
Desvantagens: complexidade, uso intensivo de recursos, desafios adicionais de governança de dados e integração de dados.

### Quando usar um data store?
Um data store é um repositório para armazenar dados. Dividido em 7 categorias: BD relacional, BD não relacional, Data Store (sistema de arquivos, armazenamento key-value, full-text search engine, fila de mensagens, in-memory data store).
Sistemas de arquivos: local ou rede (ntfs, fat, nas, san); distribuídos: HDFS, object storage; na nuvem: amazon s3, azure blob storage, google storage, delta lake; 
Armazenamento key-value: outra maneira de armazenar dados não relacionais é um armazenamento de chave-valor (dicionário em python). Redis e Memcached;
Full-Text Search Engine: pesquisar documentos de texto. Elasticsearch
Fila de mensagens: age como um middleware; ferramenta de transferência de dados, Apache Kafka.
In-memory Data store: sistemas que armazenam, leem, gravam e acessam dados na memória de acesso aleatório (RAM) em vez de na memória somente leitura (ROM), Redis, VoltDB, SAP Hana.

#### O que é um sistema distribuido?
Um sistema distribuido é uma rede de computadores que trabalham juntos como um único sistema, e que pode ser usado para armazenamento, processamento ou ambos. Projetados para compartilhar recursos e cargas de trabalho de vários computadores, permitindo que dimensionem e lidem com cargas de trabalho maiores do que um único computador poderia fazer sozinho. 
Como vamos gerenciar as tarefas computacionais em diversos computadores distribuídos?
Sistema de Arquivos Local (NTFS, ext4, APFS): um sistema de arquivo local não foi desenvolvido para ambiente distribuido. Precisamos de uma camada de software para um sistema distribuído. Precisariamos de uma camada para um sistema de arquivos distribuido, capaz de gerenciar o armazenamento de forma distribuída pelo sistema, e um sistema de processamento distribuído, capaz de ler e gravar dados do sistema de armazenamento distribuído e realizar o processamento usando a capacidade computacional oferecida pelas máquinas.
##### Hierarquia de um sistema distribuído:






