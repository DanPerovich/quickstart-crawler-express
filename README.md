# Quickstart Repo Crawler Express

This tool allows you to schedule repo crawler jobs quickly on any standard linux system

Additional info can be found [here](https://cyral.com/docs/v3.0/policy/repo-crawler/install/)

## Install

You'll need to clone this git repository (or download/extract) on to a basic linux system and run the `install.sh` script.

``` bash
git clone https://github.com/cyral-quickstart/quickstart-crawler-express.git
cd quickstart-crawler-express
sudo ./install.sh
```

## Configuration

Configuration can be done in a few simple steps

1) Login to your Control Plane
    1) Get an API Key
        1) From the bottom left select `API Access Keys`
        1) Select the `+` to add a new key
        1) Give it a name and select the following permissions
            * View Datamaps
            * Modify Policies
            * View Sidecars and Repositories
            * Modify Sidecars and Repositories
            * Repo Crawler
        1) Save the produced ID/Secret
    1) Setup a Data Repo
        1) If you haven't already, [add a Data Repo](https://cyral.com/docs/manage-repositories/repo-track)
1) SSH to the Instance you installed the Crawler on
    1) Run `crawler`
    1) Configure the control plane information
    1) Configure the repo
    1) Configure Data / Account jobs

Once the Job has successfully run you can see if the job successfully reporting by going to `Data Repos > Your Repo > Data Map > Auto Updates`

## Logs

Logs will only be stored for the last job run and will be located at `~/.local/cyral` and will be in the format of `<jobname>.log`

## Concepts

Control Plane Configuration - This is the info required to communicate the results back to the control plane.
Repo Configuration - This is related to the Data Repo configuration on the control plane and where the results will be pushed
Database Discovery Jobs - This is configuration related to specific databases that live on the Data Repo for Data Classification
Local Account Discovery Jobs - This will scan the Data Repo for any defined local accounts and will populate them in the Control Plane under that Data Repo

### Config Files

All config files will by default end up at `~/.local/cyral`
`controlplane.env` Contains all of the control plane connection info
`repo.<repo name>.env` Contains the Repo configuration
`db.<repo name>.<db name>.env` Contains the DB name for data classification discovery
