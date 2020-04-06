# package_name

ADD VERSIONEER

TODO:
1. Modify `environment.yml` with your supported Python version
2. Review dependencies to install via conda
3. Install conda environment `conda env create -f environment.yml`
4. Activate environment `conda activate package_name`
5. Install your package in editable mode, with all depdencies inside the conda environment `pip install --editable ".[all]"`
6. [add data files to gitignore] but let the user decide
7. Add configuration file, also include it in the zip file
8. Remember to keep your dependencies updated in setup.py and environment.yml

Requirements: [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

## Setup development environment

Once you cloned the repo:

```
bash setup.sh

# for help
bash setup.sh --help
```


For running tests you also need: `pip install ".[test]"`

For building documentation: `pip install ".[doc]"`


## Testing

This project uses [nox](https://nox.thea.codes/en/stable/) and [pytest](https://doc.pytest.org/en/2.8.7/index.html) for running tests. First, nox creates a conda environment (different from your development env created in the step above) and runs tests inside it (see `noxfile.py` for details). To run tests:

```
nox
```

To run tests in the current environment:

```
pytest
```

## Distribution

TODO: add changelog edit git tag instructions

To generate an arifact for deployment:

```
bash distribute/main/build.sh

# for help
bash distribute/main/build.sh --help
```

`build.sh` creates a [wheel](https://packaging.python.org/glossary/) from the package and zips ti along with the `environment.yml`, `setup.sh` and `Procfile`.

## Deployment


Although the usual `pip install {wheel}.whl` is supported, this project has non-Python dependencies that are better handled via `conda`, the recommended installation procedure is as follows:

```
# unzip the file generated in the previous step
unzip dist-main.zip
cd dist-main/

# create conda environment and install all dependencies
bash setup.sh
```

After setting up, the application is ready to run. `Procfile` states the commands needed to start the application.


