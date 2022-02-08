# Playbook: Airflow_Docker

Desenvolve uma DAG que executa tarefas de forma paralela em função das independências. Os dados são concatenados e salvos em ambiente local. 

# Descrição
#### Componentes utilizados:
* **Sistema operacional: windows 11 com Ubuntu 20.04 rodando em WSL2**
* **Python**
* **Docker**
* **Airflow**
* **Flower**

# Configuração
A pasta docker-airflow-igti_desafio_final contém os requisitos de ambiente para rodar o projeto.
Necessário importar pacotes que serão utilizados no arquivo dag_enade.py.
Quaisquer aplicações não presentes necessárias a execução deverão ser baixadas. 
O flower no projeto foi utilizado para acompanhar o desempenho dos "workers".

# Uso
Para iniciar a implantação, inicie o Docker:
    
    sudo service docker start

 navegue até a pasta onde se encontra o ambiente e execute:
    
    docker-compose -f docker-compose-CeleryExecutor.yml up -d --scale worker=4

O ambiente é escalável, nesta aplicação foram utilizados 4 "workers".

A configuração define o Airflow no http://localhost:8080/ .
A configuração define o Flower no http://localhost:5555/ .

* No ambiente, crie uma pasta com o nome "data" e execute a DAG.

* O Graph View deverá demonstrar todos os trabalhos em verde. Quando o status for "success", a pasta "data" deverá conter os dados baixados e os contruidos. 

* A aplicação terá: baixado, descompactado e filtrado os dados; construido os critérios de idade, cor da pele, escolaridade dos pais, estado civil, renda e juntado todos os atributos.

Para leitura dos dados utilizamos o Pandas. Dentro do ambiente execute:

    python
    >>> import pandas as pd
    >>> enade = pd.read_csv('./data/microdados_enade_2019/3.DADOS/enade_tratado.csv')
    >>> enade

