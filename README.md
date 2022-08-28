# circle_ci_tutorial

## Setup

### Create ECR Repository

``` sh
aws --profile <username> ecr create-repository \
    --repository-name ${AWS_RESOURCE_NAME_PREFIX}
```

### Delete ECR Repository

``` sh
aws --profile <username> ecr delete-repository \
    --repository-name ${AWS_RESOURCE_NAME_PREFIX} \
    --force
```

### Create ECS

``` sh
cd cloud_formation
aws --profile <username> cloudformation create-stack \
    --stack-name <stack name> \
    --template-body file://ECS_stack.yml \
    --parameters ParameterKey=PJPrefix,ParameterValue=${AWS_RESOURCE_NAME_PREFIX} \
                 ParameterKey=AWSAccountID,ParameterValue=<aws account id> \
                 ParameterKey=SecurityGroup,ParameterValue=<security group id> \
                 ParameterKey=Subnet,ParameterValue=<subnet id> \
                 ParameterKey=DockerImage,ParameterValue=<docker image name>
```

### Delete ECS

``` sh
aws --profile <username> cloudformation delete-stack \
    --stack-name <stack name>
```
