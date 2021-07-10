# Projeto Final de Spark

### Campanha Nacional de Vacinação contra Covid-19

O projeto foi dividido em dois níveis, básico e avançado. Recomendo fortemente fazer primeiro o básico e se sobrar tempo, pode aventurar no avançado.

Os exercícios podem ser feitos em qualquer linguagem e todas as questões são bem abertas, tendo várias formas de serem realizadas e interpretadas, pois a idéia é não termos projetos iguais.

O projeto deve estar no github.com, a forma de organizar o conteúdo é por sua conta, caso nunca tenha usado, este já é seu primeiro desafio.

Ao final do projeto você precisa preencher o formulário com o seu nome completo, email utilizado no treinamento e o link do github do seu projeto.


#### Link do formulário para envio:
##### https://forms.office.com/Pages/ResponsePage.aspx?id=2H_OZbilA0GZftoGjNhf1Y4a9bNsmMNEil2MBcFKJolUMFlTQVBNUVhRTVlSNVJUUDBWM0ZIRDVKQS4u

O formulário também estará na página do treinamento.

OBS: Todas as imagens de exemplo (Visualizações) são apenas para referencias, o projeto irá ter valores diferentes e as formas de se criar tabelas com dataframe/dataset das visualizações, pode ser realizado da maneira que preferir.


### Preparando o ambiente 

#### Para a criação e uso do ambiente vamos utilizar git e docker

Instalação do Docker no Linux 
    https://docs.docker.com/install/linux/docker-ce/ubuntu/

Instalação do git
    https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Instalando-o-Git

<br>
####1. Instalação do docker e docker-compose

####2. Executar os seguintes comandos, para baixar as imagens do Cluster de Big Data:
  git clone https://github.com/rodrigo-reboucas/docker-bigdata.git spark

    cd spark 
    docker-compose –f docker-compose-parcial.yml pull


####3. Iniciar o cluster Hadoop através do docker-compose
    docker-compose –f docker-compose-parcial.yml up -d

####4. Listas as imagens em execução
    docker ps -a 

### Para resolver o desafio acima iremos utilizar Pyspark


### Nível Básico:

Dados: 
https://mobileapps.saude.gov.br/esusvepi/files/unAFkcaNDeXajurGB7LChj8SgQYS2ptm/04bd3419b22b9cc5c6efac2c6528100d_HIST_PAINEL_COVIDBR_06jul2021.rar

### Referência das Visualizações:
• Site: https://covid.saude.gov.br/
• Guia do Site: Painel Geral

####1. Enviar os dados para o hdfs 
    a) Baixar os arquivos
    Após baixar os arquivos CSVs enviar para o diretório spark/input (volume no Namenode)

    $ docker cp HIST_PAINEL_COVIDBR_2020_Parte1_06jul2021.csv namenode:/input
    $ docker cp HIST_PAINEL_COVIDBR_2020_Parte2_06jul2021.csv namenode:/input
    $ docker cp HIST_PAINEL_COVIDBR_2021_Parte1_06jul2021.csv namenode:/input
    $ docker cp HIST_PAINEL_COVIDBR_2021_Parte2_06jul2021.csv namenode:/input

    b) Verificar o envio dos dados para o namenode
    #docker exec -it namenode ls /input

    c) Enviar os dados para o hdfs
    #hdfs dfs -put HIST_PAINEL_COVIDBR_202* /user/velhote/data


<br>
#### 2. Otimizar todos os dados do hdfs para uma tabela Hive particionada por município.

#####Preparar o ambiente para utilizarmos o Jupyter Notebook

    Configurar o jar do spark para aceitar o formato parquet em tabelas Hive

    #curl -O https://repo1.maven.org/maven2/com/twitter/parquet-hadoop-bundle/1.6.0/parquet-hadoop-bundle-1.6.0.jar

    #docker cp parquet-hadoop-bundle-1.6.0.jar jupyter-spark:/opt/spark/jars




3. Criar as 3 vizualizações pelo Spark com os dados enviados para o HDFS:

