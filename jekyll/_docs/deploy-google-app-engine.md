---
layout: classic-docs
title: Continuous Deployment to Google App Engine
categories: [how-to]
description: Continuous Deployment to Google App Engine
---

Note that there are a few common dependencies like the `gcloud` command line tool and Service Account authentication that are required
for all Google Cloud Platform deployments. Please see the general [Google Cloud Platform doc]({{site.baseurl}}/google-cloud-platform/) for more info.

## App Engine

Once you're finished following the above instructions on authentication linked to above, App Engine projects can be deployed using the gcloud command as follows:

    gcloud -q preview app deploy app.yaml --promote --version=staging

Note that while the gcloud command can be used to interact with your App Engine project, it does not include the App Engine SDK, which you may want if you are running local unit tests. It can be downloaded separately by doing the following:

```
curl -o $HOME/google_appengine_1.9.30.zip https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.30.zip
unzip -q -d $HOME $HOME/google_appengine_1.9.30.zip
```

## Google Managed VMs

Managed VMs projects are deployed similarly to App Engine:

    gcloud -q preview app deploy app.yaml --promote --version=staging

# Reference Repo

A sample app that deploys a project to App Engine can be found from CircleCI and runs end-to-end tests against the environment can be found [here](https://github.com/GoogleCloudPlatform/continuous-deployment-circle). It also contains a `managed_vms` branch that shows a similar project that deploys to Managed VMs. The sample app also requires an API Key to interact with the Google Books API, which is added to the project in a similar way to the Service Account.
