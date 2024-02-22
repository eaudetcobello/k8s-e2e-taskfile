# k8s-e2e-taskfile
Taskfile for running k8s e2e tests. Defaults to K8s 1.29 (See [Configuration](#configuration)).

## Prerequisites

* A Kubernetes cluster with 2 nodes.

* Install Go: `sudo snap install go --classic`

* Install Sonobuoy: `go install github.com/vmware-tanzu/sonobuoy@v0.57.1`

* Install Task: `snap install task --classic`

## Download

Run:
```
wget https://raw.githubusercontent.com/eaudetcobello/k8s-e2e-taskfile/main/Taskfile.yml
```

## Usage

Run tests:

```
task run
```

Check results:
```
task status
task extract
task results
```

Rerun last failed tests (using last created .tar.gz in the current directory):
```
task rerun-last-failed
```

Cleanup Sonobuoy resources before running `task run` or `task rerun-last-failed` again:
```
task delete
```

## Commands
```
task: Available tasks for this project:
* delete:                  Cleans up sonobuoy resources.
* extract:                 Creates a directory for the test results and extracts the latest .tar.gz to it.
* rerun-last-failed:       Rerun last test run that had failed tests.
* results:                 Show the results from the last test run.
* run:                     Run the k8s conformance e2e test suite.
* status:                  Check the status of the current test run.
```

## Configuration
The various tasks can be configured by modifying the different keys at the end of the Taskfile.yml.

These are the defaults:
```
env:
  KUBECONFIG: "/var/snap/microk8s/current/credentials/client.config"
  SONOBUOY_BIN: "sudo go/bin/sonobuoy"
  E2E_EXTRA_ARGS: "--non-blocking-taints=node-role.kubernetes.io/controller --ginkgo.v"
  K8S_VERSION: "v1.29.0"
  EXTRACT_DIR: "results"
  RESULTS_FILE: "{{.EXTRACT_DIR}}/plugins/e2e/results/global/e2e.log"
```
