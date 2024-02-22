# k8s-e2e-taskfile
Taskfile for running k8s e2e tests

## Requirements
* A Kubernetes cluster with 2 nodes.

* Install Go: `sudo snap install go --classic`

* Install Sonobuoy: `go install github.com/vmware-tanzu/sonobuoy@latest`

* Install Task: `snap install task --classic`

## Usage

Run tests: `task run`

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
