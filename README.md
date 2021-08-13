
## Dependencies on a local machine ##

`install docker`
`install docker compose`


## Installation and initialization ##

1. Clone the repo and navigate in to the working directory

2. Folders & Permissions requirements:

`mkdir ./docker/logs ./plugins ./docker/data`

`chmod -R 0775 ./docker/logs ./docker/data`

`chmod +x ./airflow.sh`

3. First time Init, database migration and create the first user account. 
`docker-compose up airflow-init`

4. Run Airflow and all services
`docker-compose up`


## Maintenance commands  ##

- Stop all Airflow containers (open a new terminal seesion)
`docker-compose down`

- Rebuild docker configuration
`docker-compose down`

`docker-compose up --build`

- Cleaning UP all containers:
`docker-compose down --volumes --rmi all`
 

## Testing and Ops ###

- Spin up an Ops container (shell, bash, testing, linux):
`./airflow bash`

- Print Airflow info:
`./airflow info`

- Lauch Airflow Python:
`./airflow python`

- Access Airflow Web UI
`localhost:8080`   username `airlflow`  password `airflow`

## Dependencies to solve ## 
  - Add your Py dependencies to `requirements-airflow.txt`
  - Adapt and install DAGs into the `dags` folder
  - Adapt and install Plugins into the `plugins` folder
  - Add a GCP credentials json file into the `keys` folder and rename it as `keys.json`
  - Update GCP connection variable with your project ID  "$AIRFLOW_CONN_GOOGLE_CLOUD_DEFAULT"`
  - Add variables to Airflow `variables\airflow-vars.json` file
  - Add variables to Docker containers `variables\docker-env-vars` file
  - If there is a custom Airflow configuration file ready, uncomment the line in Dockerfile in order to include it in the image: `COPY airflow.cfg ${AIRFLOW_HOME}/airflow.cfg`

## Import variables from local ENV -- hiding secrests ## 
- on a local machine `export VAR1='value'`

- add a variable to the `variables\docker-env-vars` file:

`VAR1=${VAR1}`, for example `AIRFLOW__CORE__FERNET_KEY=${AIRFLOW__CORE__FERNET_KEY}`, where 

