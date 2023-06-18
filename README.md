# CCSDA - Change coupling and structural dependencies analyzer
This project contains the prototype tools required to analyze structural dependencies in code changes


# Installation

## Download 
Download the source from the repository. 

## Configure
Create a "project_config" folder at the root.
You need to create one configuration file for each project that you would like to analyze.

```bash
proj_name: name of the project, this name will be set in the folders and saved databases.
proj_lang: currently Java, C++ and C, with the possibility to extend it to other languages.
repo_url: the https url path where the repository can be accessed
only_in_branch: if not set, default branch is “master”

from_tag:
to_tag:
since_date: format 'dd-mm-yyy'
to_date: format 'dd-mm-yyy'

path_to_proj_data_dir: relative target path where the analytics data will be saved
path_to_src_files: absolute path where git cache files will be saved
```

**Notes:** 
- Only one type of time setting can be used, either tags or dates. When using tags, both from and to tags must be set. When using dates, it is possible to only set the since_date, all changes from the given since_date to either the to_date or the current date of execution will be analyzed.
- Examples of configuration files for public git projects can be found in folder *project_config*



## Usage

### Docker
You can start the analysis of a git project using Docker.

```bash
# installation
docker-compose build

# running
docker-compose run --rm cli -C [PATH_TO_CONFIG_FILE]

# testing / linting
docker-compose run --rm --entrypoint '' cli poetry run pytest
```
Example:
```bash
docker-compose run --rm cli -C ./project_config/glucosio_small.pconfig
```
PATH_TO_CONFIG_FILE must be written with slashes.

### Poetry
Alternativelly to using docker, you can run the analysis of a git project using Poetry.

```bash
# installation
poetry install
# running
poetry run python -m CCSD.CCSD -C [PATH_TO_CONFIG_FILE]
# testing / linting
poetry run pytest
```

## Analytics and Visualization Libraries

To display the results obtained after running the application, you can start the Jupyter Notebooks contained in folder *notebooks*.
If the default folder structure of the project has not been changed, you need only to change the proj_name to match that of the project configuration file.

```bash
proj_name = 'glucosio-android' # 'PX4-Autopilot' #'PROJ_NAME'
```

The python virtual environment created by poetry can be used to already have all dependencies installed.
The location can be determined with the command `poetry env info`.

The different analytic functions are saved on the notebooks to display different characteristics of the change coupling and structural dependencies based on an *apriori* algorithm to find rules of related changed items.



[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![GitHub issues](https://img.shields.io/github/issues/GLopezMUZH/ChangeCoupling_StructuralDependencies_Analyzer)](https://github.com/GLopezMUZH/ChangeCoupling_StructuralDependencies_Analyzer/issues)
[![GitHub forks](https://img.shields.io/github/forks/GLopezMUZH/ChangeCoupling_StructuralDependencies_Analyzer)](https://github.com/GLopezMUZH/ChangeCoupling_StructuralDependencies_Analyzer/network)

[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=alert_status)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=ncloc)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=coverage)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=sqale_index)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=reliability_rating)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=duplicated_lines_density)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=vulnerabilities)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=bugs)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=security_rating)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=sqale_rating)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
[![](https://sonarcloud.io/api/project_badges/measure?project=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer&metric=code_smells)](https://sonarcloud.io/summary/overall?id=GLopezMUZH_ChangeCoupling_StructuralDependencies_Analyzer)
