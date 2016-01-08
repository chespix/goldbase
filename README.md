to get yourself going:

* clone the repo
* run these commands

```keyname="your-ec2-keypair-name"
az1="choose-an-availabilty-zone"
az2="choose-a-different-availabilty-zone-in-same-region"
dbpass="a-secure-password"

aws cloudformation create-stack --stack-name goldbase-$(date +%Y%m%d%H%M%S) \
  --template-body file://main-webapp-linux.json \
  --disable-rollback \
  --capabilities="CAPABILITY_IAM" \
  --parameters \
    ParameterKey=pKeyName,ParameterValue=$keyname \
    ParameterKey=pRegionAZ2Name,ParameterValue=$az1 \
    ParameterKey=pRegionAZ1Name,ParameterValue=$az2 \
    ParameterKey=pCreateCloudTrail,ParameterValue=false \
    ParameterKey=pDBPassword,ParameterValue=$password```
