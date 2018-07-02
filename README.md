# InputFlow
Refactored Online System for the INPUT Project

## Installation

You need a Python >= 3.5 environment.
For Windows the simplest option might be to use the [Anaconda installer](https://conda.io/docs/user-guide/install/windows.html).

Then open an Anaconda Prompt and create and activate a [virtual environment](https://conda.io/docs/user-guide/tasks/manage-environments.html) (we call ours `inputflow`):

```
conda create --name inputflow python=3.6
activate inputflow
```


Extract the current version of InputFlow to some directory.
Then switch to the InputFlow directory and install the requirements:

```
cd c://PATH/TO/INPUTFLOW
pip install -r requirements
```
cd c://Users/danie/Anaconda3/envs/inputflow/Lib/site-packages/pip/_vendor/packaging

Last we need to customize the directory from which inputflow reads its data.
This is the directory the PatientTrainingTool saves its data to.
So if your data is stored in directories like this:
```
c:/INPUT/Data/Klaus1/DATA/DAQ/20170301_150639
```
Then the easiest way is to edit `custom_data.json` and make it look like this:
```
{
    "data_source": {
        "base_dir": "c:/INPUT/Data",
        "subjects": "Klaus1"
  }
}
```

## Running
Inputflow is run from the same anaconda prompt as before. And remember to activate the `inputflow` environment and change to the inputflow directory:
```
activate inputflow
cd c://PATH/TO/INPUTFLOW
```


### Training
```
python train -p with custom_data.json idsia2
```

### Diagnostic Plots
```
python check -p with custom_data.json idsia2
```

This should save some diagnostic plots to
```
c://PATH/TO/INPUTFLOW/saved/[SubjectName]_[date]/figures
```

### Running the live system
Running the system in live mode requires the Michelangelo GUI to be running and sending the EMG data via UDP.

InputFlow can then be started like this (after it has been trained):
```
python run -p with custom_data.json idsia2
```


### Customization
Many settings can be changed very easily from the commandline.
For example `idsia2` is the name of the current best NN framework. But you can change that to `idsia1`, `lda`, or `linear_regression` to get other methods.

Changing the subject name can be done by adding `data_source.subjects=Michael` to the commandline.

