
# reSources
- builders - https://cloud.google.com/build/docs/cloud-builders
- configs - https://cloud.google.com/build/docs/configuring-builds/create-basic-configuration
- steps - https://cloud.google.com/build/docs/build-config#build_steps

# Desc

This repository is a sample configuration for integration testing with YugaByte database for Google Cloud Build.  
To run application testing against the cluster database, "sidecar" (or "service" in terms of GitLab CI) technique is required. As for now, Google Cloud Build doesn't allow to spin-up sidecar services for build steps directly. Docker Compose could be used to overcome this problem.

In this case testing application should be included to docker-compose file to run set of tests and exit. To teardown cluster on test app exit, `--abort-on-container-exit` should be passed to `docker-compose` command line (see cloudbuild.yaml).


# Deployment
- make docker-compose image for Cloud Build
``` bash
git clone https://github.com/GoogleCloudPlatform/cloud-builders-community.git
cd cloud-builders-community/docker-compose
gcloud builds submit --config=cloudbuild.yaml .
```
- submit Cloud Build build with YB RF1 cluster in Compose
`gcloud builds submit --config cloudbuild.yaml`
