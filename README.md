# Tracking Ukrainian localization progress

For details see [this issue](https://github.com/kubernetes/website/issues/20786)

## For New Contributors

1. Assign to one of [most wanted issues](https://github.com/kubernetes-i18n-ukrainian/website/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+no%3Aassignee+label%3A%22most+wanted%22) or [any non-assigned issue](https://github.com/kubernetes-i18n-ukrainian/website/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+no%3Aassignee).
2. Make fork of [k/website](https://github.com/kubernetes/website).
3. Read [Localization guidelines](https://kubernetes.io/uk/docs/contribute/localization_uk/).
4. Translate.
5. Create PR to [k/website](https://github.com/kubernetes/website).

### Help

If you need any help - join `#kubernetes-docs-uk` channel in [Kubernetes Slack](https://slack.k8s.io/) and feel free to ask.

### Exiting localization problems/updates

If you found any issues with translated content - [create issue in k/website](https://github.com/kubernetes/website/issues/new/choose) with `/language uk`.

[kubernetes-i18n-ukrainian/website](https://github.com/kubernetes-i18n-ukrainian/website) should be used only for simplify localization progress.


## Running the website locally using Docker

The recommended way to run the Kubernetes website locally is to run a specialized [Docker](https://docker.com) image that includes the [Hugo](https://gohugo.io) static website generator.

> If you are running on Windows, you'll need a few more tools which you can install with [Chocolatey](https://chocolatey.org). `choco install make`

> If you'd prefer to run the website locally without Docker, see [Running the website locally using Hugo](#running-the-website-locally-using-hugo) below.

If you have Docker [up and running](https://www.docker.com/get-started), build the `kubernetes-hugo` Docker image locally:

```bash
make docker-image
```

Once the image has been built, you can run the website locally:

```bash
make docker-serve
```

Open up your browser to http://localhost:1313 to view the website. As you make changes to the source files, Hugo updates the website and forces a browser refresh.

## Running the website locally using Hugo

See the [official Hugo documentation](https://gohugo.io/getting-started/installing/) for Hugo installation instructions. Make sure to install the Hugo extended version specified by the `HUGO_VERSION` environment variable in the [`netlify.toml`](https://github.com/kubernetes/website/blob/master/netlify.toml#L10) file.

To run the website locally when you have Hugo installed:

```bash
make serve
```

This will start the local Hugo server on port 1313. Open up your browser to http://localhost:1313 to view the website. As you make changes to the source files, Hugo updates the website and forces a browser refresh.


## Code of conduct

Participation in the Kubernetes community is governed by the [CNCF Code of Conduct](https://github.com/cncf/foundation/blob/master/code-of-conduct.md).
