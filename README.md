# Applying Neural Network Models for School-aged Children Undernutrition Classification and Feature Selection
This is a thesis project that extends the work of [Siy Van et al. (2022)](https://doi.org/10.1016/j.nut.2021.111571) by applying neural network models to predict undernutrition among school-aged children using a combination of individual and household risk factors.

![Tests](https://github.com/ongyiumark/predicting-undernutrition/actions/workflows/tests.yml/badge.svg)
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

## Contributors
- [Mark Kevin A. Ong Yiu](https://github.com/ongyiumark)
- [Carlo Gabriel M. Pastor](https://github.com/AQ51)
- [Justin M. Tan](https://github.com/bullybutcher)