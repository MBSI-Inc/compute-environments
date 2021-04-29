# Creating a `MedspaCy` Environment

While the instructions tell us `MedspaCy` works with `spaCy` 2.3 and not 3.0 it does not tell us that it does not work with Python 3.9. I also could not get Medspacy and Scispacy to be installed simultaneously.

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

## [What Did We Create?](exporting.md)
