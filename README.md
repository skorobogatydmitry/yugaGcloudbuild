
#  Google CloudBuild guides
- builders - https://cloud.google.com/build/docs/cloud-builders
- configs - https://cloud.google.com/build/docs/configuring-builds/create-basic-configuration
- steps - https://cloud.google.com/build/docs/build-config#build_steps

# Description

This repository is a sample configuration for integration tests with YugaByte database for Google Cloud Build.

To run application testing against the cluster database, "sidecar" (or "service" in terms of GitLab CI) technique is required. As for now, Google Cloud Build doesn't allow to spin-up sidecar services for build steps directly. Docker Compose could be used to overcome this problem.

Test system (TS, scripts that needs to connect to YugaByte DB) should be included to docker-compose file. TS container should work this way: run set of tests and exit. To teardown cluster on TS completion, `--abort-on-container-exit` should be passed to `docker-compose` command line (see [cloudbuild.yaml](cloudbuild.yaml)).

# Configuring

- make docker-compose image for Cloud Build
``` bash
git clone https://github.com/GoogleCloudPlatform/cloud-builders-community.git
cd cloud-builders-community/docker-compose
gcloud builds submit --config=cloudbuild.yaml .
```
- include your TS application in *docker-compose.yaml* in place of `sampleapps` service
- submit Cloud Build build: `gcloud builds submit --config cloudbuild.yaml`
