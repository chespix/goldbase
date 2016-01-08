# Goldbase Quick Start :money_with_wings:

If you want to try the Goldbase CloudFormation stacks, this is way easier than figuring out what you need to do from that pdf.

Prereqs:

* AWS Account
* Git installed
* AWS CLI installed and configured

To get yourself going:

* clone this repo
* change the variable values below
* run the cloudformation command

```keyname="your-ec2-keypair-name"
az1="choose-an-availabilty-zone"
az2="choose-a-different-availabilty-zone-in-same-region"
dbpass="a-secure-password"
# if you already have cloudtrail set up, leave this as false
newaccount=false

aws cloudformation create-stack --stack-name goldbase-$(date +%Y%m%d%H%M%S) \
  --template-body file://main-webapp-linux.json \
  --disable-rollback \
  --capabilities="CAPABILITY_IAM" \
  --parameters \
    ParameterKey=pKeyName,ParameterValue=$keyname \
    ParameterKey=pRegionAZ2Name,ParameterValue=$az1 \
    ParameterKey=pRegionAZ1Name,ParameterValue=$az2 \
    ParameterKey=pCreateCloudTrail,ParameterValue=$newaccount \
    ParameterKey=pDBPassword,ParameterValue=$password```
