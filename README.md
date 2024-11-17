# Airflow

## O que é

Este projeto utiliza o Apache Airflow para orquestração de workflows. Ele inclui a configuração de um ambiente Airflow com PostgreSQL e Redis, além de um DAG de exemplo chamado `smooth`.

## Estrutura do Projeto

``` sh
├── assets/
│ └── local-airflow-diagram.png
├── aws-proposal/
│ └── airflow-aws.png
│ └── README.md
├── dags/
│ └── smooth.py
├── logs/
│ └── .gitkeep
├── plugins/
│ └── .gitkeep
└── requirements/
│  └── run.txt
├── .gitignore
├── compose.yaml
├── LICENSE
├── PROBLEMS.md
├── README.md
```

## Configuração do Ambiente

O projeto utiliza Docker Compose para configurar os serviços necessários. O arquivo [compose.yaml](compose.yaml) define os seguintes serviços:

- **PostgreSQL**: Banco de dados para o Airflow.
- **Redis**: Broker para o Celery Executor.
- **Airflow Webserver**: Interface web do Airflow.
- **Airflow Scheduler**: Responsável por agendar as tarefas.
- **Airflow Worker**: Executa as tarefas agendadas.
- **Airflow Triggerer**: Gerencia os triggers.
- **Flower**: Interface web para monitoramento do Celery.

## Requisitos

- Docker
- Docker Compose

## Instalação

1. Clone o repositório:

    ```sh
    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>
    ```

2. Crie e ative um ambiente virtual:

    ```sh
    python -m venv .venv
    source .venv/bin/activate
    ```

3. Instale as dependências:

    ```sh
    pip install -r requirements/run.txt
    ```

4. Inicie os serviços:

    ```sh
    docker-compose up -d
    ```

## DAG de Exemplo

O projeto inclui um DAG de exemplo chamado `smooth`, definido no arquivo [dags/smooth.py](dags/smooth.py). Este DAG utiliza o operador `SmoothOperator` para executar uma tarefa chamada `youtube_video`.

## Problemas Conhecidos e Soluções

Veja o arquivo [PROBLEMS.md](PROBLEMS.md) para uma lista de problemas conhecidos e suas soluções.

## Licença

Este projeto está licenciado sob a Licença Apache 2.0. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
