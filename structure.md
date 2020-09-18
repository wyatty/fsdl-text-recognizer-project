# Code Structure (self-contained within each Lab dir)

## text_recognizer (<project>)
Everything here allows you to create a fully-functioned model 
- inference ready, trained
- Preprocessing and postprocessing
- Hyperparameters
(Bulk of the code lives here)

### datasets
Logic for downloading, preprocessing, augmenting, and loading data (no raw data here)
-> Have raw data live externally to codebase

### models
Logic for constructing Neural Networks (dumb input / output mappings)
Wraps NNs and add functionality like loss functions, saving/loading, training, (human-interpret) pred.s
-> Separating model from arch saves a lot of code duplication
-> Ex: Specific CNN arch (input images, output predictions), then logic for creating lives here

### networks
Architecture for different NNs and different hyperparameters (wrapped by `model`)


### tests
Regression tests for model code; Ensures model performance/reliability
-> Ex: Ensures a trained model performs well on important examples
-> Ex: Bias tests


### weights
Contains weights of trained production model
-> Weights for whatever version of the model that we’re using in production right now


### character_predictor.py (<project> inference wrapper)
Wrapper for a model that allows it to recognize a single character
Models are usually used in a batch setting, this allows you to input 1 example & get 1 prediction
-> That function that will be used in production


### util.py
Various utilities
-> Ex: ?


---

## training
Logic for running training; 
Running training in a scalable and easy/convenient way
-> Ex: specifying h.params on the CLI
-> Ex: how you run h.param sweeps


## notebooks
Exploring data


## tasks
Convenient scripts for what you’ll do a lot (training commands, running frequent tests)

