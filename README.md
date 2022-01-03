# Sample Application

## Set up local dev environment

```bash
# ensure pip is installed
python -m ensurepip

# create virtual environment
python -m venv .pyenv

# activate virtual environment
source .pyenv/bin/activate
# when using fish as shell (as I do)
set VIRTUAL_ENV "(pwd)/.pyenv"
```

## Build image

> `docker`, `podman` or `buildah` is needed. 

```bash
docker build --no-cache=true \
  --build-arg BUILD_TIMESTAMP=(date --iso-8601=seconds) \
  --build-arg COMMIT_SHA='insert value here' \
  -t application .
```
