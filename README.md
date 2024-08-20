***Creating Sample DAG for first inspection.

### Set Airflow directory
export AIRFLOW_HOME=~/airflow


### Installation
AIRFLOW_VERSION=2.9.1

# Extract the version of Python you have installed. If you're currently using a Python version that is not supported by Airflow, you may want to set this manually.
# See above for supported versions.
PYTHON_VERSION="$(python -c 'import sys; print(f"{sys.version_info.major}.{sys.version_info.minor}")')"

CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
# For example this would install 2.9.1 with python 3.8: https://raw.githubusercontent.com/apache/airflow/constraints-2.9.1/constraints-3.8.txt

pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"

pip install "apache-airflow==AIRFLOW_VERSION=2.9.1" --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-AIRFLOW_VERSION=2.9.1/constraints-3.9.txt"


## intialiase the airflow
docker compose up airflow-init -> runs init in docker compose
docker compose to run platform -> starts platform

## added airflow-connection service in docker-compose.yml
calls airflow cli to add connection to the database feed by environment variables

## Pipeline building
put dags in the dags folder -> your Python files
they will be automatically shown in the apache web using

## To do Database scaffold for content tables after initialising the database
sqlacodegen postgresql://airflow:airflow@postgres:6024/airflow > models.py

## To register the server within pgadmin
user: airflow
password: airflow