# circle_ci_tutorial

## Setup

### Create ECS

``` sh
cd cloud_formation
aws --profile <username> cloudformation create-stack \
    --stack-name <stack name> \
    --template-body file://ECS_stack.yml \
    --parameters ParameterKey=PJPrefix,ParameterValue=<project name> \
                 ParameterKey=AWSAccountID,ParameterValue=<aws account id> \
                 ParameterKey=SecurityGroup,ParameterValue=<security group id> \
                 ParameterKey=Subnet,ParameterValue=<subnet id> \
                 ParameterKey=DockerImage,ParameterValue=<docker image name>
```

### Delete ECS

``` sh
aws --profile privateUser cloudformation delete-stack \
    --stack-name <stack name>
```
