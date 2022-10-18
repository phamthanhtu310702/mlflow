# Hyperparameter Tuning at Scale
* Understanding automatic HPO for DL pipelines
* Creating HPO-ready DL models using Ray Tune and MLflow
* Running the first Ray Tune HPO experiment with MLflow
* Running Ray Tune HPO with Optuna and HyperBand
 ## Ray Tune

 ### In practice, we want to select a suitable HPO framework using the following five criteria:
### Callback integration with MLflow: 
- to Manage the MLflow tracking for each trial run. ```MLflowLoggerCallBack and @mlflow_minxin```. 

- Ray Tune supports both the Python mixin decorator and callback integration with MLflow. 

- mixin is a pattern that allows a standalone function to be mixed in whenever needed. This can turn any training function into a Ray Tune trainable function, automatically configuring MLflow and creating a run in the same process as each Tune trial. 
- You can then use the MLflow API inside the training function and it will automatically get reported to the correct run. 
- it supports MLflow's autologging, which means that all of the MLflow tracking information will be logged into the correct trial.

- we can add TuneReportCallback as one of the callbacks, which will pass the metrics back to Ray Tune, while the MLflow autologging does its job of logging all the tracking results simultaneously.
###  Scalability and support of GPU clusters: 
- Ray Tune supports parallel and distributed HPO through the Ray distributed framework natively.
### Ease of use and flexible APIs: 
- 
### Integration with cutting edge HPO algorithms (CS and CE):
- Ray Tune supports all cutting- edge searching methods, including the following:
    
    DragonFly, which is a highly scalable Bayesian optimization framework

    BlendSearch
- it is possible for Ray tune to continue to integrate and support any emerging schedulers or pruners in a timely fashion.
### Support of DL frameworks:
- Ray Tune has integration with popular DL frameworks such as PyTorch Lightning and TensorFlow/Keras.

## Creating HPO-ready DL models with Ray Tune and MLflow
- **Objective function**: An objective function can be either to minimize or maximize some metric values for a given configuration of hyperparameters. This objective function needs to be wrapped as a trainable function, where Ray Tune can do HPO
- **Function-based APIs and class-based APIs**: A function-based API allows a user
to insert Ray Tune statements into the model training function (called trainable in Ray Tune) such as tune.report for reporting model metrics
- **Trials**: Each trial is a run of a specific configuration of hyperparameters. This can be executed by passing the trainable function into tune.run, where Ray Tune will orchestrate the HPO process.
- **Search space**: This is a set of configurations where each hyperparameter will be assigned a way in which to sample from certain distributions
- **Suggest**:  Ray Tune provides integration to many popular open source search algorithms and can automatically convert the search space 
- **Scheduler**: Since early stopping or pruning can significantly speed up the HPO process, it is highly recommended that you use a scheduler in conjunction with a searcher: such as ASHA, HyperBand, and more.