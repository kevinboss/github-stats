# Setup and Configuration

## Installation

1. Create a personal access token (not the default GitHub Actions token) using
the instructions [here](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token).
The personal access token must have `read:user` and `repo` permissions. Copy
the access token when it is generated; if you lose it, you will have to
regenerate it. Some users report that a new personal access token can take a
few minutes to work (see [#30](https://github.com/jstrieb/github-stats/issues/30)).
2. Click [here](https://github.com/jstrieb/github-stats/generate) to create a
copy of this repository. This is not the same as forking because it copies
everything fresh without the commit history.
3. If you are reading this in your copy, open the [Secrets page](../../../settings/secrets/actions).
Otherwise, go to the "Settings" tab of the newly-created repository and open
the "Secrets" page.
4. Create a new secret named `ACCESS_TOKEN` and paste the copied personal
access token as the value.
5. Optionally configure exclusions using the secrets and environment variables
listed below.
6. Go to the [Actions page](../../../actions?query=workflow%3A"Generate+Stats+Images")
and press "Run workflow" on the right side of the screen to generate images for
the first time. The workflow regenerates images on a schedule (daily at 00:05
UTC in [`.github/workflows/main.yml`](../.github/workflows/main.yml); hourly in
upstream) and can be manually regenerated at any time.
7. Check out the images created in the [`generated`](../generated) folder.
8. Link back to [jstrieb/github-stats](https://github.com/jstrieb/github-stats)
so that others can generate their own statistics images.
9. Star the repository if you like it.

## Secrets and environment variables

- `ACCESS_TOKEN` (required secret): personal access token with `read:user` and
`repo` scopes.
- `GITHUB_ACTOR` (required environment variable): GitHub username to analyze.
GitHub Actions sets this automatically during workflow runs; set it manually
when running locally.
- `EXCLUDED` (optional secret): comma-separated repositories in `owner/name`
format (for example `jstrieb/github-stats`) to ignore.
- `EXCLUDED_LANGS` (optional secret): comma-separated languages to ignore
(matched case-insensitively).
- `EXCLUDE_FORKED_REPOS` (optional environment variable): set to `true` under
the `env` header in [`.github/workflows/main.yml`](../.github/workflows/main.yml)
(or the [upstream workflow](https://github.com/jstrieb/github-stats/blob/master/.github/workflows/main.yml))
to show statistics only for owned repositories and not forks with
contributions. Any non-empty value other than `false` enables this option; this
repository sets it to `true` by default.

## Running locally

Install the Python dependencies and run either script with a personal access
token and GitHub username:

```bash
python3 -m pip install -r requirements.txt

# Generate generated/overview.svg and generated/languages.svg
ACCESS_TOKEN=<token> GITHUB_ACTOR=<username> python3 generate_images.py

# Print collected statistics to stdout without rendering SVGs
ACCESS_TOKEN=<token> GITHUB_ACTOR=<username> python3 github_stats.py
```
