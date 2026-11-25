# [GitHub Stats Visualization](https://github.com/jstrieb/github-stats)

<a href="https://github.com/jstrieb/github-stats">

![](https://github.com/jstrieb/github-stats/blob/master/generated/overview.svg)
![](https://github.com/jstrieb/github-stats/blob/master/generated/languages.svg)

</a>

Generate visualizations of GitHub user and repository statistics using GitHub
Actions.

This project queries the GitHub GraphQL and REST APIs in GitHub Actions to
generate SVG cards for repository READMEs or a [Profile
README](https://docs.github.com/en/github/setting-up-and-managing-your-github-profile/managing-your-profile-readme).
The cards show stars, forks, all-time contributions, lines of code changed,
two-week views, contributed repositories, and language usage by file size.
Because the workflow runs in your repository with your personal access token,
it needs no external server and can include private repositories.

To set up the workflow on GitHub Actions:

1. Create a [personal access token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)
with `read:user` and `repo` scopes.
2. [Create a repository from this template](https://github.com/jstrieb/github-stats/generate).
3. Save your token as `ACCESS_TOKEN` on the
[Secrets page](../../settings/secrets/actions).
4. Select "Run workflow" on the
[Actions page](../../actions?query=workflow%3A"Generate+Stats+Images").

Embed the generated images in any README:

```markdown
![](https://github.com/<user>/<repo>/blob/master/generated/overview.svg)
![](https://github.com/<user>/<repo>/blob/master/generated/languages.svg)
```

Or install locally and run the scripts:

```bash
python3 -m pip install -r requirements.txt

# Generate generated/overview.svg and generated/languages.svg
ACCESS_TOKEN=<token> GITHUB_ACTOR=<username> python3 generate_images.py

# Print statistics to stdout without writing SVGs
ACCESS_TOKEN=<token> GITHUB_ACTOR=<username> python3 github_stats.py
```

See [docs/configuration.md](docs/configuration.md) for filtering and setup
options, [docs/limitations.md](docs/limitations.md) for API and privacy
caveats, and [docs/background.md](docs/background.md) for background.

## How to contribute

Test changes locally with `github_stats.py` and `generate_images.py`, then open
a pull request. See [CONTRIBUTING.md](CONTRIBUTING.md) for setup and layout.
