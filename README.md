# Introduction
This is the experiments code lib for knowledge graph assisted sensing data generation.

# Code Architecture
The architecture of the codes follows such a tree:

    .
    ├── data \\ store the sensor data
    │   └── WKGO \\ a specific file to store all files of WKGO
    ├── metadata \\ store the metadata, that are .ttl files
    ├── results \\ store the exmperiment results
    ├── saved_model \\ store the trained models
    └── exp
        ├── data_provider \\ initialize the data providers
        ├── model \\ initialize the generation models
        ├── embed \\ some embedding classes
        ├── data_clean \\ functions specific to individual csv files
        ├── utilize \\ some general toolkit functions
        ├── plot \\ visualization functions
        ├── exp_{} \\ a specific experiment interface
        └── run \\ the entrance of the experiments, it calls exp_{}

# Experiment 1
## Baseline
Task: Given a week of data, generate the data of next week.

Model: LSTM model is OK.

Training Data: different types of sensing data (e.g. temperature, flowrate, etc.) of ONE chiller.

Testing Data: the sensing data of ONE temperature sensor of this chiller, note that this sensor should not be used to train the model.

## Our solution
Most config is the same with the baseline, excludes:

Input: we need an extra input that embeds the type information of the sensor.
