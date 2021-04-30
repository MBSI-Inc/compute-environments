# Creating a `MedspaCy` Environment

While the instructions tell us `MedspaCy` works with `spaCy` 2.3 and not 3.0 it does not tell us that it does not work with Python 3.9. I also could not get Medspacy and Scispacy to be installed simultaneously. No worries with this, however. We can just create two different environments: one for scispacy the other for medspacy. This is a very common scenario.

Here is the `environment.yml` file I got `MedspaCy` installed with:

```Yaml
name: mbsi_medspacy
channels:
  - conda-forge
dependencies:
  - python=3.8
  - jupyterlab
  - spacy=2.3
  - pip
  - pip:
    - pyrush
    - medspacy
    - https://github.com/abchapman93/spacy_models/raw/master/releases/en_info_3700_i2b2_2012-0.1.0/dist/en_info_3700_i2b2_2012-0.1.0.tar.gz
```

To make a truly useful environment, we will need more tools. We will need a means of getting data as well as some some machine learning and visualization tools.

- `scikit-learn`
- `seaborn`
- `gensim`
- `keras`

I've created a more complete `environment.yml` file which has been added to the repository. You can build this environment and then test it with the following two notebooks:

- [medspacy.ipynb](medspacy.ipynb): Reads in the reports, randomly selects a report and does named entity recognition with general and medical-specific language models. You will see how important the medical-specific language model is.
- [db_to_files.ipynb](db_to_files.ipynb): Identifies reports in the database for a simple machine learning task and writes the data out in a format better suited for typical machine learning pipelines.

## [What Did We Create?](exporting.md)
