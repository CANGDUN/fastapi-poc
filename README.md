# fastapi-poc

## Run in local

```sh
pip install -r requirements.txt
uvicorn app.main:app --reload
```

## How to deploy to AWS Fargate

```sh
docker build -t fastapi-poc:latest .
aws ecr create-repository --repository-name fastapi-poc
aws ecr get-login-password --region "$REGION" | docker login --username AWS --password-stdin "$AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com"
docker tag fastapi-poc:latest "$AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com/fastapi-poc:latest"
docker push "$AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com/fastapi-poc:latest"
```

- Create Task Definition
- Create Service
