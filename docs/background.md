# Background

When someone views a profile on GitHub, it is often because they are curious
about a user's open source projects and contributions. Stars, forks, and pinned
repositories do not necessarily reflect the contributions a user makes to
private repositories, nor do they present a complete picture of total
contributions beyond the current year.

This project collects profile and repository statistics using the GitHub API
and generates images that can be displayed in repository READMEs or in a user's
[Profile README](https://docs.github.com/en/github/setting-up-and-managing-your-github-profile/managing-your-profile-readme).

Because the project runs on GitHub Actions, no server is required to regularly
regenerate the images with updated statistics. Because the user runs the
analysis code themselves via GitHub Actions, they can use their GitHub access
token to collect statistics on private repositories that an external service
cannot access.

This project is currently a work-in-progress; there will always be more
interesting stats to display.

## Related projects

- Inspired by a desire to improve upon
[anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
- Makes use of [GitHub Octicons](https://primer.style/octicons/) to match the
GitHub UI

## Support the project

There are a few ways to support the upstream project.

Star the repository and follow the author on GitHub. These actions motivate
continued sharing of projects and show that the work is appreciated. Consider
sharing the project on platforms like Reddit and Twitter.

Stars on GitHub also help gauge who makes use of the project, since it includes
no tracking or analytics. You can also reach out via the author's
[contact page](https://jstrieb.github.io/about/#contact) and say "hello".

If you want to spend money to show your support, consider making a donation to
one of the following organizations advocating for Internet freedoms:

- [Electronic Frontier Foundation](https://supporters.eff.org/donate/)
- [Signal Foundation](https://signal.org/donate/)
- [Mozilla](https://donate.mozilla.org/en-US/)
- [The Internet Archive](https://archive.org/donate/index.php)
