# Limitations and Privacy

## Private repository leakage

If the project is used with an access token that has sufficient permissions to
read private repositories, it may leak details about those repositories in
error messages. For example, the `aiohttp` library used for asynchronous API
requests may include the requested URL in exceptions, which can leak the name
of private repositories. If there is an exception caused by `aiohttp`, that
exception is viewable in the Actions tab of the repository, and anyone may be
able to see the name of one or more private repositories.

## GitHub API inaccuracies

Due to issues with the GitHub statistics API, it can return inaccurate results.
Repository view count statistics (which GitHub also limits to the past 14 days)
and total lines of code modified are often inaccurate. These values become more
accurate over time as GitHub caches statistics for your repositories.
Repositories that were last contributed to more than a year ago may also be
omitted due to API limitations.

For more information on inaccuracies, see issues
[#2](https://github.com/jstrieb/github-stats/issues/2),
[#3](https://github.com/jstrieb/github-stats/issues/3), and
[#13](https://github.com/jstrieb/github-stats/issues/13).
