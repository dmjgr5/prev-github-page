---
layout: post
title: Deploying a Python Flask Web Application using GCP
category: 03_Cloud
tag: [Flask, GCP, Python]
---
This document have been referred to the guide from https://codelabs.developers.google.com/codelabs/cloud-vision-app-engine/index.html?index=..%2F..index#0


----



![example](/assets/images/flask.jpg)


- Access to console.cloud.google.com
- Make a new project
- Google Cloud Shell
    - ` gcloud auth list`
    - `gcloud config list project`
      -  ` project = uplifted-time-263613`

- Get the Sample Code
  - clone git sample repository
  -   git clone https://github.com/GoogleCloudPlatform/python-docs-samples.git `
  - go to cd python-docs-samples/codelabs/flex_and_vision

- Enable APIs
    - `gcloud services enable vision.googleapis.com`
    - `gcloud services enable storage-component.googleapis.com`
    - `gcloud services enable datastore.googleapis.com`
- Authenticate API Requests
    - Enable Vision API
      - `gcloud services enable vision.googleapis.com`
    - Generate Service Account Credentials
export PROJECT_ID=[uplifted-time-263613]
    - Access the Google Cloud APIs
      - `gcloud iam service-accounts create codelab --display-name "My Codelab Service Account"`
    - Give Permission
      - `gcloud projects add-iam-policy-binding uplifted-time-263613 --member serviceAccount:codelab@uplifted-time-263613.iam.gserviceaccount.com  --role roles/owner`
    - create a Service Account key:
      - `gcloud iam service-accounts keys create ~/key.json \`
      - `> --iam-account codelab@uplifted-time-263613.iam.gserviceaccount.com`
    - Set service account key in  environment variable
      - `export GOOGLE_APPLICATION_CREDENTIALS="/home/dcjames_park/key.json"`


- Testing the Application Locally
  - Starting Your Virtual Environment and Installing Dependencies
  - Create an isolated Python 3 environment named env with virtualenv:
    - `virtualenv -p python3 env`
  - Enter your newly created virtualenv named env:
source env/bin/activate
  - Use pip to install dependencies for your project from the requirements.txt file:
    - `pip install -r requirements.txt`
  - Creating an App Engine App
    - `gcloud app create`
  - Creating a Storage Bucket
    - `export CLOUD_STORAGE_BUCKET=uplifted-time-263613
gsutil mb gs://uplifted-time-263613
python main.py`
     - choose "Preview on port 8080."

- Deploying the App to App Engine Flexible
   - `gcloud app deploy`
  - `https://< PROJECT_ID >.appspot.com`
- Clean Up GCP
    - Go to the Cloud Platform Console.
    - Select the project you want to shut down, then click ‘Delete' at the top: this schedules the project for deletion.

