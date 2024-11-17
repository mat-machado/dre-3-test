# Alterações para fix do projeto

## Problemas e Soluções

1. Scheduler não consegue se conectar ao banco devido a usuário incorreto:
    Fix: **alterado o usuário 'admin' para 'airflow' no serviço do postgres. [compose.yaml](https://github.com/mat-machado/dre-3-test/blob/fe5ac890424b8035c743ba8733cf421761ec7bb7/compose.yaml#L31)**

2. Serviço de Webserver finalizando após falha de HealthCheck:
    Fix: **alterado a porta do HealthCheck do Webserver de xxxx para 8080. [compose.yaml](https://github.com/mat-machado/dre-3-test/blob/fe5ac890424b8035c743ba8733cf421761ec7bb7/compose.yaml#L59)**

3. Serviço do Scheduler não iniciava por não encontrar a pasta 'dags':
    Fix: **alterado a pasta 'dag' para 'dags'. [compose.yaml](https://github.com/mat-machado/dre-3-test/blob/fe5ac890424b8035c743ba8733cf421761ec7bb7/compose.yaml#L14)**

4. Serviço do Scheduler não iniciava por erro de permissão da pasta 'logs':
    Fix: **executado o seguinte comando: `sudo mkdir -p ./logs && sudo chown -R 5000:5000 ./logs && sudo touch ./logs/.gitkeep`. Afim de criar a pasta de logs com as permissões necessárias.**

5. Erro ao serializar a Dag pelo scheduler:
    Fix: **adicionado `:` à função para resolver um problema de sintaxe. [smooth.py](https://github.com/mat-machado/dre-3-test/blob/fe5ac890424b8035c743ba8733cf421761ec7bb7/dags/smooth.py#L13)**

6. Durante o desenvolvimento da Dag, pacotes do Airflow não encontrados:
    Fix: **criado o arquivo `requirements/run.txt` contendo a dependência `apache-airflow==2.5.1`.
      Criado um novo ambiente virtual e instalado a dependência: `python -m venv .venv && source .venv/bin/activate && pip install -r requirements/run.txt`**
