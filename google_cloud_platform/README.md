# Google Cloud Platform

## Installation

To use google cloud, you should download gcloud tools [official website] (https://cloud.google.com/sdk/docs/quickstart) and install it.

```bash
  $ gcloud init
  # Create new project
  $ gcloud projects create bigdata-platforms-lab-2021
  
  # Set at default working project
  $ gcloud config set project bigdata-platforms-lab-2021
```

Some useful commands for gcloud are as follows:
```bash
  # Check information
  $ gcloud info
  
  # Set region and zone for the current project
  $ gcloud config set compute/region us-east4
  $ gcloud config set compute/zone us-east4-c
  
  # List google account that is active
  $ gcloud auth list

```


## Create service account 