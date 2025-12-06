# P41_Project
## Quick summary : 
1. App: Python Flask app / returns {"timestamp": "<iso>", "ip": "<client ip>"}.
2. Docker: Multi-stage / slim image; create non-root user; docker build . and docker run -p 8080:8080 <image>.
3. Publish: Push image to Docker Hub (or any public registry).
4. Terraform: terraform/ contains a module to create VPC (2 public/2 private), ALB in public subnets, ECS cluster + Fargate service running the published image in private subnets, tasks identified in private subnets only.
