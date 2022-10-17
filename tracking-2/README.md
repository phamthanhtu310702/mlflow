#  Tracking Code and Data Versioning
* Tracking pipeline versioning
* Tracking locally, privately built Python libraries
* Tracking data versioning in Delta Lake

## Pipeline Tracking
Define MLproject file:

* define evry entry point (each componet of pipeline)

* In parameters sections, there is one parameter called 'pipeline_ steps', which allows the user to define a comma-separated list of DL pipeline steps to execute. And then we define the rest of the pipeline.

* Next, we implement a Python function to execute the pipeline in main.py

* 'click' helps to parse command-line arguments

* run_pipeline() runs mlflow.start(). Each step in pipeline is executed within the mlflow.start().
    ```
    with mlflow.start_run(run_name='pipeline', nested=True) asactive_run:
    ```
    * 'nested' allows us to invioke the entry point of pipeline 

* Each step is correspoding to a file .py. We have 3 files download_data.py, fine_tuning_model.py, and register_model.py.

* The main idea here is that for each pipeline step task, it needs to start with mlflow.start_ run to launch an MLflow experiment run.

* we need to log some parameters using mlflow.log_parameter.

* We also want to set a tag to indicate which step is executed using mlflow. set_tag.

* log_artifiact: Log all the contents of a local directory as artifacts of the run. If no run is active, this method will create a new active run.

* mlflow.run(".", "download_data",parameters={}) invokes the entry point 'download data in MLproject file defined before'