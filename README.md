# Action ECR Push

> Composite action to build, tag and push docker image to private ECR Registry.
> 
> **Repository should be created manually**

# Usage

Create configuration file in `.github/workflows` directory
```yaml
name: Push to ECR

on: [push]

jobs:
  ecr-push:
    runs-on: ubuntu-latest
    name: Build and Push Docker Image to ECR
    steps:
      - uses: Bowery-RES/action-ecr-push@v1.1
        with: 
          aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }} # required
          aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }} # required
          image_tag: <image-tag> # required
          ecr_repository: <project-name> # required
          path: ./server # optional
          github_token: <personal-access-token> # optional Necessary only when repo uses submodules
```