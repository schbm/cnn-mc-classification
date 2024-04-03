# cnn-mc-classification
small comparison of different cnn for multiclass image classification

## Prerequisites

### Miniconda

To use this project with win_amd64 use [Miniconda](https://docs.anaconda.com/free/miniconda/).
We used the following version: `Conda 24.1.2 Python 3.12.1 released Feb 27, 2024`

For this project use the generated conda environment.yml file:
```
conda env create -f environment.yml
```
It includes the following dependencies:
- Python 3.10.x
- Tensorflow (2.10.0)
- Numpy
- Pandas
- Matplotlib


### Dataset
[Animal Species Classification - V3](https://www.kaggle.com/datasets/utkarshsaxenadn/animal-image-classification-dataset) with `CC0: Public Domain` license. 

In the notebook set the `data_path` variable or set the os env `aiap_data_path`to the path to the data directory.
Only keep the subdirectory of the classes you want to train on.
In our case we use the ten classes:
- Cow
- Dog
- Elephant
- Gorilla
- Hippo
- Lizard
- Monkey
- Panda
- Tiger
- Zebra

# Project Structure
- Doc
    - Contains documentation and the final report
- Notebook 
    - Contains all python jypiter notebooks