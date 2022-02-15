# go-scm

Package scm provides a unified interface to multiple source code management systems including GitHub, GitHub Enterprise, Bitbucket, Bitbucket Server, Gitee, Gitea and Gogs.

## Note on the fork

Forked from original drone/go-scm to merge jenkins-x/go-scm client factory and some minor related changes. 

It'd be great if both projects could work together, but for now trying to get the best of both and keeping this for separated.


## Useful links

Here are some useful links to providers API documentation:

- [Bitbucket cloud API](https://developer.atlassian.com/cloud/bitbucket/rest/intro/)
- [Bitbucket server/Stash API](https://docs.atlassian.com/bitbucket-server/rest/5.16.0/bitbucket-rest.html)
- [Gitea API](https://gitea.com/api/swagger/#/)
- [Gitee API](https://gitee.com/api/swagger/#/)
- [Github API](https://docs.github.com/en/rest/reference)
- [Gitlab API](https://docs.gitlab.com/ee/api/api_resources.html)
- [Gogs API](https://github.com/gogs/docs-api)

## Release procedure

Run the changelog generator.

```BASH
docker run -it --rm -v "$(pwd)":/usr/local/src/your-app githubchangeloggenerator/github-changelog-generator -u ocraviotto -p go-scm -t <secret github token>
```

You can generate a token by logging into your GitHub account and going to Settings -> Personal access tokens.

Next we tag the PR's with the fixes or enhancements labels. If the PR does not fulfill the requirements, do not add a label.

Run the changelog generator again with the future version according to semver.

```BASH
docker run -it --rm -v "$(pwd)":/usr/local/src/your-app githubchangeloggenerator/github-changelog-generator -u ocraviotto -p go-scm -t <secret token> --future-release v1.15.2
```

Create your pull request for the release. Get it merged then tag the release.
