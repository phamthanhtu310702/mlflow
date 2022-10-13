# Tracking model, parameters and metrics


* Setting up a full-fledged local MLflow tracking server
* Tracking model provenance
* Tracking model metrics
* Tracking model parameters 

## Setting up a full-fledged local MLflow tracking server
* The benefit of having a model registry is that we can register the model, version control the model, and prepare for model deployment into production.

[Postgres](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwi3urrbmtz6AhUmTmwGHShwDAYQFnoECAwQAQ&url=https%3A%2F%2Fmedium.com%2Fnoodle-labs-the-future-of-ai%2Fintroduction-to-mlflow-for-mlops-part-3-database-tracking-minio-artifact-storage-and-registry-9fef196aaf42&usg=AOvVaw16HhPPuc5rZ7WJULGO1kSp)/MySQL backend store for mlflow: 
* Use Postgres/MySQL Backend Store and Minio Artifact Store for Easy Collaboration
*  Instead of having a local mlruns folder for storing the information from MLflow Tracking, we store the parameters and metrics in a PostgreSQL/MySQL Database, while storing the artifacts in Minio object storage.

## Set Up 
1. Direct to mlflow_docker_setup subfloder
    ```
    bash start_mlflow.sh
    ```
2. Go to http://localhost/ to see the MLflow UI web page. 
3. MinIO artifact store web UI:http://localhost:9000/
    * Access Key: minio
    * Secret Key: minio123

4. Stop the server
    ```
    bash stop_mlflow.sh
    ```
## Implementing MLflow model tracking