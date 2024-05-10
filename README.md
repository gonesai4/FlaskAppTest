# FlaskAppUTest

- Unittesting project for Python Rest API Flask based

- This project is using Python 3.6.9, which may sometimes be an issue while using latest OS's.
In-case if you are facing issues with the Python version, the GitHub code will work with Python 3.8.0 also.
So you need to install that version with cmd: pyenv install 3.8.0
And, in the jenkins script just replace 3.6.9 with 3.8.0.
pyenv global 3.8.0

## Jenkins CI Pipeline Cmds:

#!/bin/bash
source ~/.bashrc
pyenv versions

pyenv global 3.8.0

echo "#### Create venv and activate it python version 3.8.0 ####"
python3 -m venv flaskapp
source flaskapp/bin/activate
python3 -V

echo "##### Install required Python Modules ####"
pip install -r requirements.txt

# Cobertura - Code Coverage
pip install coverage
pip install pytest-cov

echo '#### Run tests ####'
pytest --cov=main --cov-report xml

pytest utests --junitxml=./xmlReport/output.xml

echo "##### Deactivate venv and reset python version to system ####"
deactivate
pyenv global system
python3 -V
