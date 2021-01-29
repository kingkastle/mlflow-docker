FROM jupyter/pyspark-notebook

RUN python --version
RUN pip install -U boto3 mlflow Minio

COPY .env .env
COPY Leads.csv /work/Leads.csv
COPY MLflow.ipynb /work/MLflow.ipynb
COPY bashrc_install.sh bashrc_install.sh

USER root
RUN chmod +x bashrc_install.sh
RUN chmod +rw /work/*
RUN chmod 777 /work
RUN ./bashrc_install.sh

ENV SPARK_HOME=/usr/local/spark/
ENV PATH=$PATH:/usr/local/spark/bin

WORKDIR /work
