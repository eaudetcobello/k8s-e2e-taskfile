# k8s-e2e-taskfile
Taskfile for running k8s e2e tests

## Requirements
Install Go: `sudo snap install go --classic`
Install Sonobuoy: `go install github.com/vmware-tanzu/sonobuoy@latest`
Install Task: `snap install task --classic`

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
