
ARG AIRFLOW_IMAGE_NAME="apache/airflow:2.1.2"
FROM ${AIRFLOW_IMAGE_NAME}

#COPY airflow.cfg ${AIRFLOW_HOME}/airflow.cfg

# INSTALL TOOLS & DEPENDENCIES
COPY requirements-airflow.txt  requirements.txt
RUN pip3 install -r requirements.txt 