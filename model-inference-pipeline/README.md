# Model Inference Pipeline

- Understanding patterns of DL inference pipelines
- Understanding the MLflow Model Python Function API
- Implementing a custom MLflow Python model
- Implementing preprocessing and postprocessing steps in a DL inference pipeline
- Implementing an inference pipeline as a new entry point in the main ML project

## Understanding patterns of DL inference pipelines
While the model has been trained, tuned, and tested on curated offline datasets, now it needs to handle prediction in two ways:
- **Batch inference**: 
- **Online inference**: 

While the pattern for inference pipelines is still emerging, it is now commonly known that there are at least four patterns in a real-world production environment:
- **Multi-step pipeline**: This is the most typical usage of the model in production, which includes a linear workflow of preprocessing steps before the model logic
is invoked and some postprocessing steps after the model evaluation results are returned. While this is conceptually simple, the implementation can still be varied.

- **Ensemble of models**: This is a more complex scenario where multiple different models can be used. These could be the same types of models with different versions for A/B testing purposes or different types of models

- **Business logic and model**: This usually involves additional business logic on how and where the input to the model should come from, such as querying from an enterprise database for user information and validation or retrieving precomputed additional features from a feature store before invoking a model.

- **Online learning**: This is one of the most complex inference tasks in production where a model is constantly learning and updating its parameters 

## Understanding the MLflow Model Python Function API
The MLflow Model is one of the core components provided by MLflow to load, save, and log models in different flavors.

