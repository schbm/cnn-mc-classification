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
- Scikit Learn


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

# Issues

```
#Removes all packages installed by pip
pip freeze > requirements.txt
pip uninstall -r requirements.txt -y
#Remove conda env and recreate using env yml.
conda env remove --name ai
```

If you encounter the following error:
```
08:00:20.754 [warn] StdErr from Kernel Process OMP: Error #15: Initializing libiomp5md.dll, but found libiomp5 already initialized.
OMP: Hint This means that multiple copies of the OpenMP runtime have been linked into the program. That is dangerous, since it can degrade performance or cause incorrect results. The best thing to do is to ensure that only a single OpenMP runtime is linked into the process, e.g. by avoiding static linking of the OpenMP runtime in any library. As an unsafe, unsupported, undocumented workaround you can set the environment variable KMP_DUPLICATE_LIB_OK=TRUE to allow the program to continue to execute, but that may cause crashes or silently produce incorrect results. For more information, please see http://www.intel.com/software/products/support/.

08:00:21.473 [error] Disposing session as kernel process died ExitCode: 3, Reason: 2024-04-04 08:00:13.315855: I tensorflow/core/platform/cpu_feature_guard.cc:193] This TensorFlow binary is optimized with oneAPI Deep Neural Network Library (oneDNN) to use the following CPU instructions in performance-critical operations:  AVX2
To enable them in other operations, rebuild TensorFlow with the appropriate compiler flags.

2024-04-04 08:00:13.321932: I tensorflow/core/common_runtime/process_util.cc:146] Creating new thread pool with default inter op setting: 2. Tune using inter_op_parallelism_threads for best performance.
OMP: Error #15: Initializing libiomp5md.dll, but found libiomp5 already initialized.
OMP: Hint This means that multiple copies of the OpenMP runtime have been linked into the program. That is dangerous, since it can degrade performance or cause incorrect results. The best thing to do is to ensure that only a single OpenMP runtime is linked into the process, e.g. by avoiding static linking of the OpenMP runtime in any library. As an unsafe, unsupported, undocumented workaround you can set the environment variable KMP_DUPLICATE_LIB_OK=TRUE to allow the program to continue to execute, but that may cause crashes or silently produce incorrect results. For more information, please see http://www.intel.com/software/products/support/.
```
Add the following env variable:
```
os.environ['KMP_DUPLICATE_LIB_OK']='True' #Workaround for kernel crash because multiple copies of the OpenMP runtime have been linked
```
This allows the program to work with multiple linked OpenMP runtimes. This may lead to problems.

## Exporting Env
```
conda env export > environment.yml
```