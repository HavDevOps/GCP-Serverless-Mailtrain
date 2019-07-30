Note: This Tutorial is Incomplete; It's a Work in Progress

#### Steps:
Depending on how you have configured your system and Docker you may need to prepend the commands below with `sudo`.

* Download Mailtrain files using git: `git clone https://github.com/mrhavens/GCloudTrain.git` and open Mailtrain folder `cd GCloudTrain`
* Modify `docker-compose.override.yml` and modify it if you need to.
* Bring up the stack with: `docker-compose up -d`
* Start: `docker-compose start`
* Open [http://localhost:8080/](http://localhost:8080/) (change the host name `localhost` to the name of the host where you are deploying the system).
* Authenticate as user `admin` with password `test`

* If everything looks good, we continue on to the Gcloud deployment...

If not already done, make sure Gcloud is set up and up to date:

* gcloud components install beta
* gcloud components update

In GCloudTrain directory with Docker file, :

* gcloud builds submit --tag gcr.io/PROJECT-ID/gcloudtrain

Where PROJECT-ID, you should put your google cloud project ID (all lower case).

gcloud beta run deploy --image gcr.io/PROJECT-ID/gcloudtrain --platform managed
Please specify a region:
 [1] us-central1
 [2] cancel
Please enter your numeric choice:  1

To make this the default region, run `gcloud config set run/region us-central1`.

Service name (mailtrain):  gcloudtrain
Allow unauthenticated invocations to [gcloudtrain] (y/N)?  y

Deploying container to Cloud Run service [gcloudtrain] in project [PROJECT-ID] region [us-central1]
⠛ Deploying new service... Deploying Revision.                         
  ⠛ Creating Revision... Deploying Revision.
  . Routing traffic...
  ✓ Setting IAM Policy...

Build and deploy mysql container
* gcloud builds submit --tag gcr.io/PROJECT-ID/mysql
* gcloud beta run deploy --image gcr.io/PROJECT-ID/mysql

Build and deploy redis container
* gcloud builds submit --tag gcr.io/PROJECT-ID/redis
* gcloud beta run deploy --image gcr.io/PROJECT-ID/redis

