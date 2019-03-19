# Gruntwork Helm Charts for Kubernetes

This repository holds the index file for [the Gruntwork Helm Repository](https://helmcharts.gruntwork.io), served using
[GitHub pages](https://pages.github.com/). The index file serves to hold the list of available helm charts distributed
by Gruntwork, including the associated metadata that describes the charts. You can read more about the repository index
file from the [official documentation](https://helm.sh/docs/developing_charts/#the-index-file).

This repository does not contain any of the charts; only references to the charts that are stored in other GitHub
repositories. You can find the list of repositories in the [Charts](#charts) section of this document. For information
on the reasoning behind this setup, you can refer to the [Why are the charts in a different
repository?](#why-are-the-charts-in-a-different-repository) section.


## How do you install the charts in this Repo?

You can access these charts by adding the Gruntwork Helm Repo to your client:

```bash
$ helm repo add gruntwork https://helmcharts.gruntwork.io
```

Then, you can access any of the charts under the `gruntwork` name. For example, you can find all the Gruntwork charts by
searching for `gruntwork`:

```bash
$ helm search gruntwork
```

In general, each of the charts document the required and optional input values in the corresponding `values.yaml` file.
You can access the `values.yaml` of a Chart either by inspecting this repository, or using the `helm inspect` command.
For example, to see the values of the `k8s-service` chart, you can run:

```bash
$ helm inspect values gruntwork/k8s-service
```

Once you know what values the chart requires, you can install the chart by defining your own `values.yaml` file with the
required values defined. Then, you can install the chart to your Kubernetes cluster using `helm install`:

```bash
$ helm install -f values.yaml gruntwork/k8s-service
```

See the `helm install` help text for more configuration options.


## Charts

### Kubernetes Services Helm Charts

These charts help you package your applications for deployment into Kubernetes. The code for the charts are available in
the [gruntwork-io/helm-kubernetes-services](https://github.com/gruntwork-io/helm-kubernetes-services/) github
repository.

- [k8s-service](https://github.com/gruntwork-io/helm-kubernetes-services/blob/master/charts/k8s-service)


## Why are the charts in a different repository?

The source code for the charts are managed in separate repositories. By storing the charts in separate repositories, we
are able to:

- Release and version the charts using GitHub releases. By doing so, we can setup a CI/CD pipeline that automatically
  generates the chart package with a related index file.
- Make testing easier. By having repositories that only manage a small number of charts, we are able to better test the
  charts by having faster CI cycles.
- Have examples and documentation that integrates multiple charts together. By having groups of charts under different
  themed repositories, we are able to provide better examples that require combining multiple charts together.


## How to deploy the index file

The index file is automatically deployed from the `master` branch.

Currently construction of the index file is a manual process. Eventually, this will be enhanced to automatically
generate the index file when there is a new release in the source repositories.

To add new charts:

- Release a new version on the source repository containing the helm chart.
- Wait for the CI build to append the index file and chart packages.
- Download the generated index file.
- Merge the index file with the existing one in this repo:
    * If an entry already exists append the list entry to the existing one.
    * For new entries, add to the `entries` map under the same heading.


## License

Copyright (c) 2019 Gruntwork, Inc

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
