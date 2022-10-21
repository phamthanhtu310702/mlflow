# Deploy a Model at scale
- Understanding the landscape of deployment and hosting environments
- Deploying locally for batch and web service inference
- Deploying using Ray Serve and MLflow deployment plugins

## Understanding different deployment tools and host environments
Now, let's look at what kind of tools are available for deploying model inference as a service, especially those tools that have support for MLflow model deployment. There are three types of model deployment and serving tools, as follows:
- **MLflow built-in model deployment**: This comes out of the box from MLflow releases, which includes deployments to a local web server.
- **MLflow custom deployment plugins**: MLflow provides an API for deploying to custom serving environments through MLflow deployment plugins. We will show how to use the ```mlflow-ray-serve``` plugin for deployment in this chapter.
- **Model serving tools that can deploy MLflow model flavors**: These are usually generic model serving frameworks that support many types of models, including MLflow model flavors. Examples include ***Seldon MLServer***, ***Ray Serve***. We will show you how to use Ray Serve together with the mlflow-ray-serve plugin to deploy the MLflow Python mode