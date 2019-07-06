#### Steps:
Depending on how you have configured your system and Docker you may need to prepend the commands below with `sudo`.

* Download Mailtrain files using git: `git clone git://github.com/Mailtrain-org/mailtrain.git` (or download [zipped repo](https://github.com/Mailtrain-org/mailtrain/archive/master.zip)) and open Mailtrain folder `cd mailtrain`
* Copy the file `docker-compose.override.yml.tmpl` to `docker-compose.override.yml` and modify it if you need to.
* Bring up the stack with: `docker-compose up -d`
* Start: `docker-compose start`
* Open [http://localhost:3000/](http://localhost:3000/) (change the host name `localhost` to the name of the host where you are deploying the system).
* Authenticate as user `admin` with password `test`
* Navigate to [http://localhost:3000/settings](http://localhost:3000/settings) and update service configuration.
* Navigate to [http://localhost:3000/users/account](http://localhost:3000/users/account) and update user information and password.

Make sure Gcloud is set up and up to date:

* gcloud components install beta
* gcloud components update

In mailtrain directory with Docker file, :

* gcloud builds submit --tag gcr.io/PROJECT-ID/mailtrain

Where PROJECT-ID, you should put your google cloud project ID (all lower case).

gcloud beta run deploy --image gcr.io/PROJECT-ID/mailtrain --platform managed
Please specify a region:
 [1] us-central1
 [2] cancel
Please enter your numeric choice:  1

To make this the default region, run `gcloud config set run/region us-central1`.

Service name (mailtrain):  mailtrain
Allow unauthenticated invocations to [mailtrain] (y/N)?  y

Deploying container to Cloud Run service [mailtrain] in project [PROJECT-ID] region [us-central1]
⠛ Deploying new service... Deploying Revision.                         
  ⠛ Creating Revision... Deploying Revision.
  . Routing traffic...
  ✓ Setting IAM Policy...
