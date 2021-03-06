# Lab 9 - NSX-T Pipeline Install

## Overview

Concourse is an Open source CI/CD pipeline tool used to perform Day 1 and 2 Ops on the CNA platform.
The NSX-T Pipeline was created to provide our customers a simple way to deploy NSX-T (end to end) in a few clicks, with a repeatable deployment process.

In this lab you will setup Concourse and then run a pipeline to install NSX-T

## Concourse setup and NSX-T Pipeline Kickoff

Concourse can be stoodup in many different ways. In this lab we will stand it up using a combination of docker images with docker-compose.

### Prereq's: (Already have been installed)

- Ubuntu 16.04 or later
- Docker 18.06 or later
- Docker-compose
- Git
- Fly

1.0 SSH to the cli-vm

<details><summary>Screenshot 1.0</summary>
<img src="Images/ssh-cli-vm.png">
</details>

1.1 Navigate to the concourse directory where the docker-compose.yml file is located.

`cd concourse`

<details><summary>Screenshot 1.1</summary>
<img src="Images/concourse-dir.png">
</details>

1.2 Use docker-compose to stand up the pipeline and web server.

`docker-compose up -d`

<details><summary>Screenshot 1.2</summary>
<img src="Images/docker-compose-up.png">
</details>

1.3 Verify that all 4 containers are in the **Up** status and that none have *Exited*

`docker ps`

<details><summary>Screenshot 1.3</summary>
<img src="Images/docker-ps.png">
</details>

<<<<<<< HEAD
1.4 Import the NSX pipeline using the `fly` cli command on the cli-vm.
=======
1.4 Using a web browser navigate to the concourse URL

`http://cli-vm.corp.local:8080`


1.5 In the upper right-hand corner login to Concourse

- Username: nsx
- Password: vmware

<details><summary>Screenshot 1.5</summary>
<img src="Images/concourse-login.png">
</details>

1.6 Import the NSX pipeline using the `fly` cli command on the cli-vm.  The source script will create the `fly-s` alias used below to simplify the commands.
>>>>>>> 4b83042eb5d684ff5a9895bdbb90b9dd9bc39862

`cd ~/nsx-t-datacenter-ci-pipelines/pipelines`

`source nsxt-setup.sh`

`fly-s`
- confirm the parameters file import with `y`

<details><summary>Screenshot 1.4.1</summary>
<img src="Images/nsx-pipeline-dir.png">
</details>

<details><summary>Screenshot 1.4.2</summary>
<img src="Images/source-nsxt-setup.png">
</details>

<details><summary>Screenshot 1.4.3</summary>
<img src="Images/pipeline-import.png">
</details>

<details><summary>Screenshot 1.4.4</summary>
<img src="Images/confirm-import.png">
</details>

<<<<<<< HEAD
1.5 Using a web browser navigate to the concourse URL

`http://cli-vm.corp.local:8080`

<details><summary>Screenshot 1.5</summary>
<img src="Images/pipeline-ui.png">
</details>

1.6 In the upper right-hand corner login to Concourse

- Username: nsx
- Password: vmware

<details><summary>Screenshot 1.6</summary>
<img src="Images/concourse-login.png">
</details>

1.7 Confirm that the pipeline has imported and hit the **Play** button
=======
1.7 Go back to the web browser and confirm that the pipeline has imported and hit the **Play** button in the lower right hand corner of the *install-nsx-t* tile
>>>>>>> 4b83042eb5d684ff5a9895bdbb90b9dd9bc39862

<details><summary>Screenshot 1.7</summary>
<img src="Images/pipeline-ui.png">
</details>

1.8 Click on *install-nsx-t*

<details><summary>Screenshot 1.8</summary>
<img src="Images/install-nsx-t.png">
</details>

1.9 Verify that the pipeline is not in an *errored* state

- You will see Maroon colored boxes if the pipline is errored out
  - If it is in an errored state perform a `fly-d` and `fly-s` to destory and re-import the pipeline on the cli-vm.

<details><summary>Screenshot 1.9</summary>
<img src="Images/pipeline-started.png">
</details>

1.10 Click on the **install-nsx-t** light-gray box in the pipeline

<details><summary>Screenshot 1.10</summary>
<img src="Images/install-nsx-t.png">
</details>

1.11 Execute the pipeline with the **Plus** button in the upper right-hand corner

<details><summary>Screenshot 1.11</summary>
<img src="Images/install-nsx-t-plus.png">
</details>

1.12 Grab some coffee and watch the magic happen!

<img src="Images/automate-all-things.png">

1.13 After coffee :coffee: and around 45 to 60 minutes you should see this.

<details><summary>Screenshot 1.13</summary>
<img src="Images/pipeline-complete.png">
</details>
