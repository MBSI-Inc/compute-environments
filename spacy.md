# Creating a working spaCy environment

My initial attempts to simply replace nltk with `spacy=3.0`failed:

```bash
Solving environment: failed

ResolvePackageNotFound:
  - scispacy
  - spacy=3.0
```

## Diagnosis

conda could not find either `spacy=3.0` or `scispacy` in the `conda` channel. The `conda` channel is the official collection of packages created and maintained by the Anaconda corporation. Looking at the spaCy GitHub page, we can see that spaCy is available in the `conda-forge` channel; this is a community channel, containing packages contributes by the community at large rather than Anaconda.

## Action

 Change the channel to `conda-forge` and see if it works.


You should see that it doesn't complain about `spacy` anymore but it cannot find scispacy. Looking at `scispacy's` GitHub page, we see that the instructions are to use pip to install scispacy.

Modify your `environment.yml` file to use `conda` to install `pip` and then use `pip` to install `scispacy` and one of the language models listed on the [GitHub site](https://github.com/allenai/scispacy).

__Hint__: look at the example `environment.yml` file I provided.

## Action: Adding [`Medspacy`](https://spacy.io/universe/project/medspacy)

Scispacy looks really promising, but what we are really interested in is working with clinical reports. The language of biomedical literature and clinical texts are quite different, so our performance will be suboptimal if we use models trained on one to analyze the other.

Before continuing, be sure to commit your changes and create a tag `scispacy`.

- `git add environment.yml`
- `git commit -m "working environment with spacy and scispacy"`
- `git tag scispacy`

A little browsing through [spaCy Universe](https://spacy.io/universe) you find [`Medspacy`](https://spacy.io/universe/project/medspacy). Read through the installation instructions [here](https://github.com/medspacy/medspacy) and see if you can modify the `environment.yml` file to add `MedspaCy` to our compute environment.

After giving it your best shot move you can move on to the next page.

[Solution: Installing MedspaCy](medspacy.md)
