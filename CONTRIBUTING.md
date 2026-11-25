# Contributing

This guide covers local setup, verification, and repository layout for
contributing to this project.

## Prerequisites

- [Python 3](https://www.python.org/downloads/) (`.github/workflows/main.yml`
runs Python 3.12)
- [pip](https://pip.pypa.io/en/stable/installation/)
- A GitHub [personal access token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)
with `read:user` and `repo` scopes for local runs

## Setup and verification

Install the dependencies listed in `requirements.txt` (`requests` and
`aiohttp`):

```bash
python3 -m pip install --upgrade pip setuptools wheel
python3 -m pip install -r requirements.txt
```

There is no automated test suite. Run `github_stats.py` to test API queries and
print a plain-text summary, then run `generate_images.py` to write
`generated/overview.svg` and `generated/languages.svg`:

```bash
ACCESS_TOKEN=<token> GITHUB_ACTOR=<username> python3 github_stats.py
ACCESS_TOKEN=<token> GITHUB_ACTOR=<username> python3 generate_images.py
```

You can also pass `EXCLUDED`, `EXCLUDED_LANGS`, and `EXCLUDE_FORKED_REPOS` in
the environment when testing filtering behavior.

## Repository layout

- `github_stats.py`: defines `Queries` for GitHub GraphQL (v4) and REST (v3)
requests using `aiohttp` with a `requests` fallback and retries on HTTP 202
responses, and `Stats` for aggregating account and repository metrics.
- `generate_images.py`: reads environment variables, fetches `Stats`, and
renders `templates/overview.svg` and `templates/languages.svg` into
`generated/`.
- `templates/overview.svg` and `templates/languages.svg`: SVG card templates
populated by replacing `{{ ... }}` placeholders.
- `generated/overview.svg` and `generated/languages.svg`: generated SVG outputs
committed by the GitHub Actions workflow.
- `.github/workflows/main.yml`: `Generate Stats Images` workflow. Runs on push
to `master`, daily at 00:05 UTC (`5 0 * * *`), and via `workflow_dispatch`.
Uses concurrency group `generate-stats` so overlapping runs queue instead of
colliding on push.
- `requirements.txt`: Python package dependencies (`requests` and `aiohttp`).

## Pull requests

Keep changes focused, verify the script output and generated SVG files locally,
and open a pull request.
