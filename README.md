﻿# Applying XGBoost and Neural Networks in the Undernutrition Classification of School-aged Children in the Philippines
This is a thesis project that extends the work of [Siy Van et al. (2022)](https://doi.org/10.1016/j.nut.2021.111571) by applying Random Forest, XGBoost, and Neural Network models to predict undernutrition among school-aged children in the Philippines, using a combination of individual and household risk factors.

![Tests](https://github.com/ongyiumark/predicting-undernutrition/actions/workflows/tests.yml/badge.svg)

Feel free to raise an issue if you have any questions or have encountered any problems.

---

## Important Notes

### On Neural Networks with Random Forest Structure (NNRF)

- The `NNRF` package we use in this project is provided by GitHub user [`paradoxysm`](https://github.com/paradoxysm/nnrf). Unfortunately, their package requires the `sklearn` package rather than `scikit-learn`. This is the wrong package and has been [deprecated by the Scikit-Learn team](https://pypi.org/project/sklearn/). 
- As a result, on 2023 December 1st onwards, attempting to install the `sklearn` package rather than the `scikit-learn` package will always raise an exception. 
- The maintainers of this repository have already reached out to user `paradoxym` to update their requirements from `sklearn` to `scikit-learn`. Until this is resolved, we recommend forking the [`NNRF` repository](https://github.com/paradoxysm/nnrf), and using their functions directly.

### On the Local Python Package
- This repository includes a local python package, which can be viewed and edited in the `src/predunder` folder.
- You may view the documentation for this package in the `docs/_build/html` folder. Alternatively, you may read the docstrings in the source code itself.

### On Visualizing Decision Trees
- To visualize decision trees, we use the `dtreeviz` module, which requires `graphviz` binaries in the System Path. Follow the instructions provided in the [`dtreeviz`](https://github.com/parrt/dtreeviz) repository.

- We've included a `visualize_tree.py` helper program in the `code` folder. Run `visualize_tree.py -h` for more information.

---
## How to Contribute

### Setting Up

#### For Windows Users:
1. Make sure you have [Python 3.10.6](https://www.python.org/downloads/) installed. Do not install python from the windows store.
2. Clone this repository using `git clone https://github.com/ongyiumark/predicting-undernutrition.git`
3. Go inside the reposisitory using `cd .\predicting-undernutrition\`
4. Create a new python virtual environment using `py -m venv [environment name]`. For example `py -m venv thesisPU`
5. Activate the virtual environment using `.\[environment name]\Scripts\activate`. For example `.\thesisPU\Scripts\activate`
6. Make sure you have the latest version of pip using `py -m pip install --upgrade pip` 
7. Install the local package using `py -m pip install -e .`
8. Install the development dependencies using `pip install -r .\requirements_dev.txt`

#### For Unix or MacOS Users:
1. Make sure you have [Python 3.10.6](https://www.python.org/downloads/) installed.
2. Clone this repository using `git clone https://github.com/ongyiumark/predicting-undernutrition.git`
3. Go inside the reposisitory using `cd predicting-undernutrition/`
4. Create a new python virtual environment using `python3 -m venv [environment name]`. For example `python3 -m venv thesisPU`
5. Activate the virtual environment using `. [environment name]/bin/activate`. For example `. thesisPU/bin/activate`
6. Make sure you have the latest version of pip using `python3 -m pip install --upgrade pip` 
7. Install the local package using `python3 -m pip install -e .`
8. Install the development dependencies using `pip install -r ./requirements_dev.txt`


### Contribution Workflow
1. Setup the repository by following the instructions above.
2. Create a new branch using `git checkout -b [add your 2-letter initials here]--[branch code]`. For example `git checkout -b mo--edit-readme`
3. Make changes in `/src/predunder` and add tests in `/tests`
4. Run `mypy src code`, `flake8 src code tests`, and `pytest` to check for errors
5. Run `tox` to test buiding a new environment. This may take a few minutes.
6. Add and commit your changes with git
7. Push your local branch to github using `git push -u origin [branch name]`. For example, `git push -u origin mo--edit-readme`
8. Submit a pull request 
9. Tag someone to review your code
10. Merge your PR only after receiving at least 1 approval from a reviewer

---
## Program Workflow

1. Make sure to `cd` into the `code` folder.
2. Run `clean_data.py`. 
    - This reads the excel file from `data/Data.xlsx` and extracts the necessary columns into `cleaned-data/cleaned_X.csv` and `cleaned-data/cleaned_y.csv`.
3. Run `classify_data.py`. 
    - This classifies each child according to the reference standards specified in `cleaned-data/wf.xlsx`. This produces `cleaned-data/tags.xlsx` and `cleaned-data/final_tags.csv`.
4. Run `split_data.py`
    - This splits the data into a testing group and training group. This populates the `train-test-data` folder.
    - You may change the test size and the random seed of the program through command line arguments. Run `split_data.py -h` for more information.
5. Run `chi_test.py`
    - This runs $\chi^2$ tests of independence on the features and labels. This also generates latex tables in the `latex` folder.
6. Run `train_task.py`
    - This tunes hyperparameters and evaluates the models on the testing group. 
    - The best hyperparameters are stored in the `results` folder. The allows the program to skip tuning if the best hyperparameters are available. This also generates latex tables in the `latex` folder. 
    - Run `train_task.py -h` for more information. For example, to run the program on the `2aii` task, you may run the command `train_task.py -t 2aii`. To ignore the best hyperparameters, you may run the command `train_task.py -t 2aii -r`.
7. Run `combine_tables.py`
    - As the name suggests, this combines all the tables into a single latex file. This is to make copy-pasting easier.

---

## Maintainers

### Lead Maintainer
- [Mark Kevin A. Ong Yiu](https://github.com/ongyiumark)

### Contributors
- [Carlo Gabriel M. Pastor](https://github.com/AQ51)
