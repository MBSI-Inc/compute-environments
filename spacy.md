# Creating a working spaCy environment

My initial attempts failed:

```bash
Solving environment: failed

ResolvePackageNotFound:
  - scispacy
  - spacy=3.0
```

## Diagnosis

conda could not find either `spacy=3.0` or `scispacy` in the `conda` channel. The `conda` channel is the official collection of packages created and maintained by the Anaconda corporation. Looking at the spaCy GitHub page, we can see that spaCy is available in the `conda-forge` channel; this is a community channel, containing packges contributes by the community at large rather than Anaconda.

## Action

 Change the channel to `conda-forge` and see if it works.


You should see that it doesn't complain about `spacy` anymore but it cannot find scispacy. Lookint at `scispacy's` GitHub page, we see that the instructions are to use pip to install scispacy.

Modify your `environment.yml` file to install `pip` and then use `pip` to install `scispacy` and one of the language models listed on the [GitHub site](https://github.com/allenai/scispacy).

__Hint__: look at the example `environment.yml` file I provided.
