# POMS managed productions (analysis)

POMS stands for Production Operations Management System, and it is used to provide a highly configurable and user-friendly interface for production submission. 

Anyone in ICARUS can submit jobs using the POMS interface. The basic is well described in the dedicated `redmine` page, which you can find [here](https://cdcvs.fnal.gov/redmine/projects/project-py). 

> `Project-py` was updated recently to be run from AL9 nodes, instead of the usual SL7 container. This is the updated guide

## Setting it up

Setting up `Project.py` executable script can be done by running the script 

```bash
source /exp/sbnd/app/users/vito/products/setup_project_py_el9.sh
```

Once done, it is now possible to use it to submit jobs. 

## Submitting jobs

Submitting jobs is done with the `Project.py` commands. Before running those it is required to have a valid token and upload it over the worker nodes.

To generate token, first it is needed to declare the `ENV` variable for the filename, and then create the token through the `htgettoken` command

```bash
export BEARER_TOKEN_FILE=/tmp/bt_u$(id -u)
htgettoken -v -a htvaultprod.fnal.gov -i icarus
```
Tokens can be uploaded using `Project.py` interface 

```bash
Project.py --experiment icarus --upload_credentials
```

At this point job configurations can be uploaded using the command 

```bash 
Project.py --experiment icarus --create_campaign --replace_campaign --cfg_file <name of cfg file>.cfg --ini_file <name of ini file>.ini
```
This will upload the configuration `.cfg` and submission `.ini` files. Once uploaded the individual stages (listed using the `Project.py --experiment icarus --show_campaigns` command) can be submitted with the command

```bash
Project.py --experiment icarus --submit --stage_id <stage id>
```