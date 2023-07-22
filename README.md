# 3.5-Assignment-HS

Authentication / Authorization to ECR

For pushing to public repositories

Permissions needed:
ecr-public:GetAuthorizationToken
sts:getservicebearertoken

Command:
aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/<registry alias>

For Private Repositories:
Permissions needed:
ecr:GetAuthorizationToken

Command:
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <aws account number>.dkr.ecr.ap-southeast-1.amazonaws.com


Command to build an image
docker build -t <IMAGE_NAME>:<IMAGE_TAG> .

Command example with my image
docker build -t simple-app-image .

Command to tag an image
docker tag <IMAGE_NAME>:<IMAGE_TAG>  <REPOSITORY_URI>:<IMAGE_TAG>

Command example with our image and repository
docker tag simple-app-image:latest <account no.>.dkr.ecr.ap-southeast-1.amazonaws.com/<REPOSITORY_NAME>:latest

Command to push image:
docker push <account no.>.dkr.ecr.ap-southeast-1.amazonaws.com/<REPOSITORY_NAME>:latest