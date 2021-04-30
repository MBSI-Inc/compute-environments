# Defining and Versioning Compute Environments

"Back when I was a child," software development was hard but uncomplicated: it was hard because you essentially had to write everything from scratch, using only the functionality provided by the core language; it was uncomplicated because I only needed to worry about what my own code did. Because we had to write everything from scratch, our programs (my programs) were relatively simple.

With the advent of software distribution via the internet, programming flipped: it is now easy but complicated. Programming is easy because instead of writing everything from scratch you can now find most of the functionality you want in the multitude of third-party libraries that are available for any language (plus the languages themselves have more high-level functionality). Programming is complicated now because all of these third-party libraries have their own dependencies and as you aggregate libraries for your application, these dependencies can create conflicts.

The complicated nature of modern computation makes reproducible computational science and engineering difficult. An important step towards making computation more reproducible is to precisely define your computing environment. This is difficult. But there are a number of important tools that can help such as [Docker](https://www.docker.com/) or [Singularity](https://sylabs.io/singularity/) for defining [containers]() and tools like [Ansible](https://www.ansible.com/) for general purpose provisioning. I _strongly_ recomend learning how to use Docker.


A first step towards _precisely_ defining our computing environment is to specify the primary pieces of a computing environment. We will do this using conda environment files.

## `conda` Environment Files

A `conda` environment file is a [YAML]() file that specifies

1. The name of the environment
1. The Anaconda _channel_ to install packages from
1. The version of Python we are going to use (e.g. 3.8.9)
1. The packages to install with `conda`
    1. We can optionally specify the version of the package to install. We want to do this, but it can be complicated to do so.
1. The packages we want to install with `pip`, for example packages not available with `conda`. __Note:__ this requires that we install `pip` with `conda`.

### Activity: Define an Environment

We are going to build a natural language processing (NLP) application for working with clinical text. You do a quick web search and you see that there are several

- [NLTK](https://www.nltk.org/)

__Latest Release:__  3.6.2

__Description:__


>NLTK is a leading platform for building Python programs to work with human language data. It provides easy-to-use interfaces to over 50 corpora and lexical resources such as WordNet, along with a suite of text processing libraries for classification, tokenization, stemming, tagging, parsing, and semantic reasoning, wrappers for industrial-strength NLP libraries, and an active discussion forum.

- [Stanza](https://stanfordnlp.github.io/stanza/index.html)

__Latest Release:__  1.2

__Description:__

>Stanza is a collection of accurate and efficient tools for many human languages in one place. Starting from raw text to syntactic analysis and entity recognition, Stanza brings state-of-the-art NLP models to languages of your choosing.

- [spaCy](https://spacy.io/)

__Latest Release:__  3.0

__Description:__


> spaCy is designed to help you do real work --- to build real products, or gather real insights. The library respects your time, and tries to avoid wasting it. It's easy to install, and its API is simple and productive.


You decide you want the latest and greatest. These are all packages from top-notch universities: Penn (NLTK), Stanford (Stanza), and MIT (spaCy), but NLTK is the oldest, highest release number so presumably the most advanced. So let's define an environment for running NLTK in Jupyterlab.

1. Create a GitHub repository named something like "mbsi-nlp-demo".
1. Clone the repository on your computer.
1. In the cloned repository, create a file named `environment.yml` and modify the example below to specify the packages we need.
    1. Use Python 3.9
    1. for `name` create a short, descriptive name that is personalized to you (e.g. uses your initials)
    1. for channels, use `conda`
    1. Only install software that you think you need.

```YAML
name: cdth_fhir
channels:
  - conda-forge
dependencies:
  - python=3.8
  - pip
  - matplotlib
  - python-dateutil
  - requests
  - seaborn
  - pip:
    - git+https://github.com/smart-on-fhir/client-py.git
```

## Switching to spaCy

You do some more reading about Python and NLP and you learn about this cool tool [scispacy](https://spacy.io/universe/project/scispacy) for NLP of the biomedical literature. This is based on spaCy rather than NLTK, so we want to switch our environment.yml to use spacy rather than NLTK and install scispacy. But since we have a working environment that we may want to return to, be sure to commit any changes you have already made in `environment.yml`. Also add and commit the NLTK test notebook. Once you've made these changes, we will create a __tag__ specifying that this latest commit contains the working code for NLTK-based NLP.

- `git tag nltk`

### Activity

Try editing the `environment.yml` file to install `spacy` instead of `NLTK` and to also install `scispacy`.

Once you have updated your `environment.yml` file run the following command

`conda env update -f environment.yml --prune`

__Note:__ I didn't run add the `--prune` argument during the grand rounds; this was a mistake. `--prune` will remove any packages that are no longer required by what is specified in the `environment.yml` file.


Once you have given it a good shot, slock on the link below to see what I did.

[spaCy Environment](spacy.md)
