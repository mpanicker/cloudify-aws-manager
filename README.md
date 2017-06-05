# instructions to install Cloudify manager on AWS
1. Download and install cloudify CLI 3.4.1 GA from(Command Line Interface) from http://cloudify.co/downloads/previous_ga_versions.html

2. open the cloudify cli desktop icon created. this opens a new command line 

3. git clone this repository and go to the folder

4. run cfy init

5. sign up for a free aws account and go to https://console.aws.amazon.com/console/home?region=us-east-1

6. click on your name on the top right hand corner to see the "My Security Credentials" drop down and click it. Under Access keys, create a new Access key. note down the access key id 
and Secret Access key. you will need it in the manager blue print

7. I have used a Centos 7 image in us-east with id ami-6d1c2007. I have used a t2.medium server which is the minimum requirement but you can use a larger one. 

i have used existing manager and agent key pair but if you are running this for the first time, set the following properties

a. comment these 2 lines
manager_keypair_name
agent_keypair_name:

b. set the following to false
use_existing_manager_group
use_existing_agent_group

c.set the following to false
use_existing_manager_keypair
use_existing_manager_keypair

d. comment these 2 lines
ssh_key_filename
agent_private_key_path

e. comment these 2 lines
manager_security_group_name
agent_security_group_name


8. run cfy bootstrap --install-plugins -p /path/to/manager/blueprint/file -i /path/to/inputs/yaml/file

9. Depending on the cloud environment and the server specifications you provided, this should take between 10 to 20 minutes to complete. After validating the configuration, cfy will create the management VM, related networks and security groups, download the relevant packages and install all of the components. At the end of this process you should see the following message:

10. run cfy status




-------------------
errors
-------------------
1. 2017-06-04 21:17:38 CFY <manager> [management_keypair_8wfu56.creation] Task failed 'ec2.keypair.creation_validation' -> Not external resource, but the key file exists locally.
2017-06-04 21:17:38 CFY <manager> 'execute_operation' workflow execution failed: Workflow failed: Task failed 'ec2.keypair.creation_validation' -> Not external resource, but the key file exists locally.
Workflow failed: Task failed 'ec2.keypair.creation_validation' -> Not external resource, but the key file exists locally.

resolution: see 7 above 