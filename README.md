
# MongoDB Deployment using Cloudformation and Ansible for 4 instance MongoDB cluster with two Replica and one Arbiter on AWS 

**This deployment is not production ready, suited to be used as minimal POC or Demo for MongoDB Database with Replication and Arbiter**
**Original deployment is on Ubuntu 20.04 with MongoDB 6.0**

## Architecture

![alt text](https://github.com/achilleus82/TMDemo/blob/main/MongoDB.png?raw=true)

## How to

1. Generate AWS Elastic IP to be used in MongodbCloudformation.yaml
2. Modify variable in inventory.ini , MongoDB.yaml and MongodbCloudformation.yaml depending on your setup 
3. Upload MongodbCloudformation.yaml using Cloudformation Console or use AWS CLI
4. Run the Ansible Playbook below

> ansible-playbook -i inventory.ini MongoDB.yaml


## Ansible Script Flow

1. Script will run on "mongodb" host specified in inventory.ini
2. Variable to be used later in script is defined. 
     - repl_name is the name of the replica set
     - members which is an array containing host,port,priority,votes and arbiter of each member of the replica set
3. Script perform a number of task in order to setup MongoDB with Replication and Arbiter
     - modify hosts file to resolve MongoDB hostname to an IP address using host file
     - perform pre requisite to install MongoDB such as import of MongoDB package repository key, adding MongoDB package repository
     - install security package repository to install libssl1.1 which is a dependency for MongoDB 6.0
     - install MongoDB community edition package
     - configuration of mongod.conf to set replication and bind ip configuration
     - start MongoDB service
     - check status of replicaset, initiate replicaset and add arbiter 

## ToDo 
    - templatize better the cloudformation and ansible to use config file


