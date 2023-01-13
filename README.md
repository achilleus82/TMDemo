
# MongoDB Deployment with two Replica and one Arbiter on AWS with Cloudformation Template

**This deployment is not production ready, purpose is to learn most basic MongoDB replication and arbiter components deployed using ansible, it is purposely made simple to facilitate learning without the "fluff"**

To use this modify inventory.ini with IP address on your infrastructure and run

> ansible-playbook -i inventory.ini MongoDB.yaml

Documentation is mostly in MongoDB yaml on comments to provide better visual run through on the process and journey. Have fun! step by step.

**Original deployment is on Ubuntu 20.04 with MongoDB 6.0 , your mileage may vary**