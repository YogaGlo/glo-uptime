# Build and Push Docker Image to AWS ECR

## Prerequisites

- Latest **AWS CLI** and **Docker** installed

## ECR Repository Information

- **Region**: `us-east-1`
- **Registry URL**: `694260482182.dkr.ecr.us-east-1.amazonaws.com`
- **Repository**: `production-glo-uptime`

## Steps

```bash
# 1. Authenticate Docker client
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 694260482182.dkr.ecr.us-east-1.amazonaws.com

# 2. Build using npm script (builds frontend + Docker image)
npm run build-docker-release-local

# 3. Tag with ECR repository name
docker tag glo-uptime:latest 694260482182.dkr.ecr.us-east-1.amazonaws.com/production-glo-uptime:latest

# 4. Push to ECR
docker push 694260482182.dkr.ecr.us-east-1.amazonaws.com/production-glo-uptime:latest
```

## Troubleshooting

- **Authentication errors**: Verify AWS credentials with `aws configure`
- **Build errors**: Ensure Node.js >= 20.4.0 and Dockerfile exists at `docker/dockerfile`
- **Push errors**: Verify image tag and repository permissions

