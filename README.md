# Gruntwork Helm Charts for Kubernetes

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
