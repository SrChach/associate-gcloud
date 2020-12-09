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

## Projects and Config

``` bash
gcloud config get-value project

gcloud projects list

gcloud config set project <project-id>

## Configuring variables for specific services
gcloud config set compute/zone <zone>
gcloud config get-value compute/region
```

You can also create, delete and control projects using the following commands

> Notice that the `<project-id>` *must* be unique at creating the project

``` bash
# Create a new project with the default credentials
gcloud projects create <project-id>

# Delete a GCP project
gcloud projects delete <project-id>
```

> **Exercise**: make a script that can run an [example script](./compute/examples/startup_example.sh) that runs an stackdriver process and logs data to a bucket on startup

Solution:

``` bash
# First, enable the stackdriver and storage services with `gcloud services enable <service>`

# Then we can create the instance with metadata that uses an startup script using `--metadata-from-file` flag 
gcloud compute instances create <instance-name> --metadata-from-file startup-script=<path/to/script.sh>

# Example
gcloud compute instances create myvm --metadata-from-file startup-script=compute/examples/startup_example.sh

## Go th
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
gsutil mb gs://<bucket-name>

# Copying things from cloud to local and viceversa
gsutil cp -r <source> <target>
gsutil mv <source> <target>

gstutil ls -r gs://<bucket-name>

gsutil rm -r gs://<bucket-name>

## Access Control List (Permissions)
gsutil acl set private gs://<bucket-name>

## Access Control List Change (Permissions -> Public)
gsutil acl ch -u AllUsers:R gs://<bucket-name>/<url-to-resource>
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

# Connecting to a Machine/Instance
gcloud compute ssh <instance-name>
```
