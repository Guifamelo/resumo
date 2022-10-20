# Aetherflow - Claimfy Airflow (Reality Gem)

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/claimfy/cfy-infinity-arc">
    <img src="https://raw.githubusercontent.com/claimfy/claimfy/main/images/eye-of-agamotto-pixel-art.png" alt="Logo" width="80" height="60">
  </a>

  <h3 align="center">Data of Agamotto</h3>

</div>

## Description
<p>
O projeto Airflow visa auxiliar na automatização dos processos existentes
na Claimfy, os quais necessitam de um orquestrador para tarefas complexas,
como por exemplo o Motor de Diligência.
</p>

## Getting Started

### Dependencies

#### Requirements

- Ubuntu 20.04
- Python3.8
- MSODBCSQL17 (Caso não esteja instalado acesse este [link](https://github.com/MicrosoftDocs/sql-docs/blob/live/docs/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md#-debian-1) para instalação)
- Tesseract (Caso não esteja instalado acesse este [link](https://lindevs.com/install-tesseract-ocr-on-ubuntu/) para instalação)
- pip3
- libpq-dev

### Instalação Airflow

Para criar o ambiente python para o Airflow, execute os comandos a seguir no terminal:

```sh
python3.8 -m venv airflow_venv
source airflow_venv/bin/activate
pip install apache-airflow['postgresql']
pip install psycopg2
```

### Configuração do Airflow

Para a configuração do acesso ao postgresql pelo Airflow, execute o comando a seguir:

```sh
export AIRFLOW__DATABASE__SQL_ALCHEMY_CONN='postgresql+psycopg2://{POSTGRES_USER}:{POSTGRES_USER_PWD}@{POSTGRES_HOST}:{POSTGRES_PORT}/{POSTGRES_DB}'
```

Onde:

- {POSTGRES_USER}: indica o usuário que o airflow utilizará para acessar o banco de dados
- {POSTGRES_USER_PWD}: indica a senha de acesso do usuário
- {POSTGRES_HOST}: indica o endereço onde o banco de dados está hospedado-
- {POSTGRES_PORT}: indica a porta do banco de dados
- {POSTGRES_DB}: indica o database que o Airflow utilizará para criar a estrutura de dados para armazenar os seus metadados.

Vale lembrar que as credenciais de acesso ao postgresql para o Airflow devem seguir  
as recomendações indicadas na documentação do Airflow. Caso não seja do conhecimento,  
segue o [link](https://airflow.apache.org/docs/apache-airflow/stable/howto/set-up-database.html#setting-up-a-postgresql-database) para as instruções.

A segunda configuração básica a ser feita é a definição do Executor. Para isso, execute o seguinte comando:

```sh
export AIRFLOW__CORE__EXECUTOR='LocalExecutor'
```

A última configuração é o apontamento para onde estão as DAGs. Execute o comando a seguir:

```sh
export AIRFLOW__CORE__DAGS_FOLDER='~/aetherflow/dag'
```

> **OBS**: Todas as configurações realizadas acima podem ser feitas no arquivo de configuração do Airflow
> chamdo airflow.cfg.

### Iniciando o Banco de Dados

Para iniciar o banco de dados para o Airflow, execute o comando a seguir:

```sh
airflow db init
```

### Criação do Usuário para o Airflow

Caso não existe um usuário já criado para o Airflow, execute o comando a seguir:

```sh
airflow users create -r Admin -u admin -e admin-email@claimfy.com.br -f FirstName -l LastName -p {password}
```

Onde:

- **-r**: indica em qual role (função) você quer criar o usuário
- **-u**: indica qual username utilizará para o usuário administrador logar no Airfloe
- **-e**: indica qual e-mail do usuário
- **-f**: indica o primeiro nome do usuário
- **-l**: indica o último nome do usuário
- **-p**: indica a senha de acesso

> **OBS**: Uma observação a ser feita sobre a senha, é que o parâmetro **-p** parte do pressuposto  
> que a senha a ser criada será uma senha não totalmente aleatório. Caso queira criar uma senha  
> totalmente aleatório, utilize o parâmetro --use_random_password. Para maiores informações utilize os links a seguir:
>
> - [Create user parameters](https://airflow.apache.org/docs/apache-airflow/stable/cli-and-env-variables-ref.html#create_repeat1)
> - [Access Control](https://airflow.apache.org/docs/apache-airflow/stable/security/access-control.html#:~:text=Airflow%20ships%20with%20a%20set,adding%20permissions%20to%20these%20roles.)
> - [WebServer Configuration](https://airflow.apache.org/docs/apache-airflow/stable/security/webserver.html)

## Instalação das bibliotecas para o funcionamento das DAGs

```sh
pip install -r requirements.txt
```

## Start Airflow

Para iniciar o Airflow, precisa ligar o webserver e scheduler.

### Ligar Webserver

```sh
{host}:8089
```

Onde o {host} indica o endereço da máquina onde o airflow está hospedado.

### Ligar Scheduler

```sh
airflow scheduler
```

### Airflow with docker

```
 sudo chmod u=rwx,g=rwx,o=rwx /home/user/airflow_logs
```

Made with ♥ by Claimfy (https://github.com/claimfy)
​
