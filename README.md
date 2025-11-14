# AWS CI/CD Pipeline for Docker + Helm

This repository deploys:

- AWS CodePipeline
- AWS CodeBuild
- Amazon ECR
- S3 Artifacts Bucket

Using CloudFormation, this repo:
1. Builds a Docker image
2. Pushes image to ECR
3. Packages Helm chart
4. Outputs packaged `.tgz` chart

## Deploy

aws cloudformation deploy \
  --template-file cloudformation/pipeline.yaml \
  --stack-name docker-helm-pipeline \
  --capabilities CAPABILITY_NAMED_IAM \
  --parameter-overrides \
      GitHubOwner=YOUR_USER \
      GitHubRepo=aws-cicd-docker-helm-pipeline \
      GitHubToken=YOUR_TOKEN
