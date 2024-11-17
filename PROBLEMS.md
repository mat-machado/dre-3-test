# Alterações para fix do projeto

## Problemas e Soluções

1. Scheduler não consegue se conectar ao banco devido a usuário incorreto:
    Fix: **alterado o usuário 'admin' para 'airflow' no serviço do postgres. [compose.yaml L31](compose.yaml)**

2. Serviço de Webserver finalizando após falha de HealthCheck:
    Fix: **alterado a porta do HealthCheck do Webserver de xxxx para 8080. [compose.yaml L61](compose.yaml)**

3. Serviço do Scheduler não iniciava por não encontrar a pasta 'dags':
    Fix: **alterado a pasta 'dag' para 'dags'. [compose.yaml L14](compose.yaml)**

4. Serviço do Scheduler não iniciava por erro de permissão da pasta 'logs':
    Fix: **executado o seguinte comando: `sudo mkdir -p ./logs && sudo chown -R 5000:5000 ./logs && sudo touch ./logs/.gitkeep`. Afim de criar a pasta de logs com as permissões necessárias.**

5. Erro ao serializar a Dag pelo scheduler:
    Fix: **adicionado `:` à função para resolver um problema de sintaxe. [smooth.py L13](dags/smooth.py)**

6. Durante o desenvolvimento da Dag, pacotes do Airflow não encontrados:
    Fix: **criado o arquivo `requirements/run.txt` contendo a dependência `apache-airflow==2.5.1`.
      Criado um novo ambiente virtual e instalado a dependência: `python -m venv .venv && source .venv/bin/activate && pip install -r requirements/run.txt`**
