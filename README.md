# LeBogoo / Workflows

## Workflows
- build-and-push: This workflow builds a docker image from a dockerfile located in the root of your project. It automatically pushes it to the github container registry.

## How to use

Make sure to enablek `Read and write permissions` for github actions workflows.
This can be done in `(Repository) Settings > Actions > General > Workflow permissions`:
<img alt="workflow-permission" src="https://github.com/user-attachments/assets/2c0438c0-56de-459b-9ad7-cbaa68c7aa3c" />

Paste this in your `.github/workflows/build-and-push.yml` file and change the image name.
```yml
name: Build and Push Docker image

on:
  push:
    branches:
      - "**"
    tags:
      - "v*"

jobs:
  build-and-push:
    uses: LeBogoo/workflows/.github/workflows/build-and-push.yml@v1.0.0
    with:
      image_name: "my_project"
    secrets:
      GHCR_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
