# Commands GCP

This repo was created for study commands for the GCP associate cert exam.
In the future, I expect to do a guide for moving smooth in GCP. But not now

## Login

``` bash
gcloud auth login

# List accounts
gcloud auth list
```

## Help

``` bash
gcloud topic <topic>

#example
gcloud topic filters
```

## Projects

``` bash
gcloud config get-value project

gcloud projects list

gcloud config set project <project-id>
```

## Services

``` bash
gcloud services list --enabled

# le podemos pasar "| grep <service>" para buscar un servicio
gcloud services list --available



## Enabling/disabling services
gcloud services enable <service>
gcloud services disable <service>
```

## Storage

``` bash
gsutil mb gs://<some-bucket-name>
```

## Compute

``` bash
gcloud compute instances list

gcloud compute instances create <instance-name>
gcloud compute instances delete <instance-name>

# example 
gcloud compute instances create <instance-name>

# whoami / hostname

gcloud compute machine-types list
gcloud compute machine-types list --filter="NAME:f1-micro AND ZONE~us-west"

gcloud compute ssh <instance-name>
```
