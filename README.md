
# Sources
- builders - https://cloud.google.com/build/docs/cloud-builders
- configs - https://cloud.google.com/build/docs/configuring-builds/create-basic-configuration
- steps - https://cloud.google.com/build/docs/build-config#build_steps

# make docker-compose repo
``` bash
git clone https://github.com/GoogleCloudPlatform/cloud-builders-community.git
cd cloud-builders-community/docker-compose
gcloud builds submit --config=cloudbuild.yaml .
```

# Build SampleApps

`gcloud builds submit --config cloudbuild.yaml`
