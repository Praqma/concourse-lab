# Running a pipeline in Concourse


The pipelines live in config files right next to your code. This way the config is committed along with your code in your version control system.

## Setup

### Download
To create a pipeline on your server (which in our case for the demo is http://138.68.100.7:8080/) you need a way to configure your pipeline. We use fly cli for that. Fly cli is a command line tool that puts your configuration on Concourse. You can get it from the server itself.
- Go on http://138.68.100.7:8080/
- login (u:concourse, pw:changeme)
- download the cli from the right bottom 3 different ones for different OS-es

For further info you can read on here: https://concourse.ci/downloads.html
https://concourse.ci/fly-cli.html

### Set target

To address a command to a specific server with fly cli, you need to set a target on it.

You can do that with the following command

- `fly --target conc-test login  --concourse-url http://138.68.100.7:8080`

where
- fly : the exe file you downloaded
- --target : setting an alias for the server, conc-test in this case
- login : will ask for login credentials as a user input after you ran the command (the same that is given in the download section)
- --concourse-url : the url of the server

## Create pipeline

In the local clone of your git repo containing your work, create a pipeline folder where you will place your pipeline description file (hello-simcorp.yml). We have done this for you in the https://github.com/SimCorpTrial/concourse-test-target.git repo.

- cd into the folder your config file is
- run the following command to put/update your pipeline on the server

  - `fly -t conc-test set-pipeline -p hello-simcorp -c hello-simcorp.yml`

### Unpause the pipeline

When a pipeline is initally created, it is paused. To unpause the pipeline, run
  - `fly -t conc-test unpause-pipeline -p hello-simcorp`
