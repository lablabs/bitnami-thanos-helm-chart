[<img src="https://cdn.prod.website-files.com/66b4bc4ca83726f5a87183ab/685136470d15399f106cb13e_adcbd542a834a1942d077cd5c09d3057_GitHub%20cover%20image%201584x396.png">](https://lablabs.io/)

**About us:**</br>
[Labyrinth Labs](https://lablabs.io/) is a one-stop-shop for **DevOps, Cloud & Kubernetes**! We specialize in creating **powerful**, **scalable** and **cloud-native platforms** tailored to elevate your business.

[As a team of experienced DevOps engineers](https://lablabs.io/about/), we know how to help our customers start their journey in the cloud, address the issues they have in their current setups and provide a **strategic solution to transform their infrastructure**.

----

# Helm chart template

This is a template reposity that should be use to create in-house Helm charts.

## Usage

### Initialize repo from template

1. Create a repo from the template.

    1. Remove directories and files specified in [`.templatesyncignore`](.templatesyncignore) as these are expected to be unique per chart.

1. Address all `FIXME config` comments to set the repository up.
1. Place your chart in [`charts`](charts) directory. You can have multiple charts.

    1. Modify [`Chart.yaml`](charts/example/Chart.yaml) accordingly!

1. Place custom values for the chart tests in [`values.yaml`](`charts/example/ci/values.yaml`).

> [!IMPORTANT]
> If your chart contains custom resources, make sure CRDs or any other dependencies are installed in Kind cluster created in the [`pull-request`](.github/workflows/pull-request.yaml) workflow and `chart-testing` job.

1. If you want to use [helm-docs](https://github.com/norwoodj/helm-docs) to generate your Helm chart documentation, modify the contents of [`README.md.gotmpl`](charts/example/README.md.gotmpl) file. helm-docs will use the file to generate [`README.md`](charts/example/README.md).
Otherwise, remove helm-docs from pre-commit and you can modify the chart README.md by hand.

### Releasing a chart

1. Install pre-commit by running `pre-commit install`.
1. Commit and create a PR. Make sure the chart version is updated appropriately in [`Chart.yaml`](charts/example/Chart.yaml).
1. Wait for actions to succeed and approval.
1. Merge PR.

### Integrate with ArtifactHUB

1. Helm chart artifacts are stores as OCI compliant packages in GitHub container registry.
1. To add Helm chart into ArtifactHUB follow <https://artifacthub.io/docs/topics/repositories/helm-charts/#oci-support>.
1. When the ArtifactHUB repo is created, copy its ID to artifacthub-repo.yaml. This will mark the repo as verified.
1. All following releases will be automatically pushed to ArtifactHUB.

## Validation, linters and pull-requests

We want to provide high quality code and modules. For this reason we are using several [pre-commit hooks](.pre-commit-config.yaml). A pull-request to the master branch will trigger these validations and lints automatically. Please check your code before you create pull-requests. See [pre-commit](https://pre-commit.com/) documentation and [GitHub Actions](https://docs.github.com/en/actions) documentation for further details.

## Contributing and reporting issues

Feel free to create an issue in this repository if you have questions, suggestions or feature requests.

## License

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

See [LICENSE](LICENSE) for full details.

```plan
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

  <https://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under
```
