# Re-Architecting-Web-App-on-AWS
Re-Architecting a multi tier java Web App on AWS Cloud [PAAS &amp; SAAS]
<img width="1523" alt="Screenshot 2023-09-23 at 2 18 34 PM" src="https://github.com/abdtarek/Re-Architecting-Web-App-on-AWS/assets/137318449/0b5d6a10-96a5-417f-9712-325d0b25b4cc">
## Comparison
BEANSTALK<------TOMCAT Ec2/VM

ELB in BEANSTALK<------NGINX LB/ELB

AUTOSCALING<------NONE / Autoscaling

EFS /S3<------NES / S3/ EFS

RDS<------MYSQL on VM/Ec2

ELASTIC CACHE<------MEMCACHED on VM/EC2

ACTIVE MQ<------RABBITMQ on VM/Ec2

ROUTE53<------GODADDY, local DNS NONE / MULTI DC ACROSS WORLD

CLOUDFRONT<------None
## Flow of Execution

- Login to aws account
- Create Key pair for beanstalk instance login
- Create Security Group for Elasticcache, RDS & ActiveMQ
- Create
  ~ RDS
  • Amazon Elastic Cache
  • Amazon Active MQ
- Create Elastic Beanstalk Environment
- Update SG of backend to allow traffic from Bean SG
- Update SG of backend to allow internal traffic
- Launch Ec2-Instance for DB Initializing
- Login to the instance and Inititialize RDS DB
- Change healthcheck on beanstalk to /login
- Add 443 https Lister to ELB
- Build Artifact with Backend Information
- Deploy Artifact to Beanstalk
- Create CDN with ssl cert
- Update Entry in GoDaddy DNS Zones
