# EMB3RS OFFLINE Lite 

Offline Standalone version of the EMB3RS platform. 

Main Features:
  - District Heating Network simulation 
  - Pinch Analysis (Internal Heat Recovery)
  - ORC design (Internal Heat Recovery)

### Input: 

Each feature need a specfic CSV, which can be obtained in the folder csv_inputs

### Output:

Currently, each simulation generates HTML reports that the user can analyze

DHN simulation reports:
  - GIS  
  - TEO
  - MM 
  - BM 
  
Pinch Analysis reports:
  - CF report
  - BM report

ORC design reports:
  - CF report
  - BM report


---

## Usage DHN Simulation

```
Terminal

clone the repo
conda env -f create environment_all.yml
conda activate new_embers_offline_v_2
git submodule update --init --recursive
git submodule update --recursive --remote

```


Simulation example code:

```python
from Embers import Embers

platform_offline = Embers()

# Get file
dhn_file_path = 'test/DHN/dhn_data.xlsx'
platform_offline.run_dhn(file_path=dhn_file_path)

# It always creates a folder ("intermediate_json_files") with json files of each module, and an output folder ("output") with the reports of each module, inside you directory - DHN, in this case.

```
As simple as that.

Extra features:
```python
from Embers import Embers

dhn_file_path = 'test/DHN/dhn_data.xlsx'

# Starting from an intermediate step? read the json files of the modules, to start from where you desire
# -> check below,the parameter:modules_data_json
cf_module_json = 'test/DHN/intermediate_json_files/cf.json'

## Run platform features - As simple as that
platform = Embers()
platform.run_dhn(file_path=dhn_file_path,
                 get_intermediate_steps_json=False,  # OPTIONAL - if you do not desire to get the modules json files from the simulation
                 not_to_run_modules=['mm', 'bm'],  # OPTIONAL - if you do not desire to run specfific modules
                 modules_data_json={"cf": cf_module_json})  # OPTIONAL - if you have already the data for the modules, and you do not need to run it

```


---
