# What Have We Created?

While we only specified a few packages, `conda` and `pip` installed quite a few packages. There is both a `pip` and a `conda` way of seeing the totality of what is installed.

### `pip freeze`

`pip freeze` lists out all the installed packages. The output from this command can be redirected (`>`) to a file, commonly named `requirements.txt`. This file can then be used by another user to replicate the environment with `pip`.

#### Save Environment

- `pip freeze >requirements.txt`

#### Install the Environment

- `pip install -r requirements.txt`

### `conda export`

#### Save Environment

The equivalent `conda` command is `conda export`
- `conda env export > environment.yml`

Alternatively if we only want to export the packages we explicitly asked for, we can add the `--from-history` argument
- `conda env export --from-history > environment.yml`
    - __Note:__ this seems to exclude what we asked for with

#### Install the Environment

- `conda env build -f environment.yml`
