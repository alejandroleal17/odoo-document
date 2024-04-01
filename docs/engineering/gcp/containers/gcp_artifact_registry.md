```markdown
# AWS and Google Cloud Image Management Workflow

## 1. Activate the Virtual Environment

Activate your virtual environment:

```bash
source .venv/bin/activate
```

## 2. Establish AWS Connection

Connect to your AWS environment:

```bash
awsume tr-dev 
Enter MFA token: **** 
```

## 3. Clone Images from AWS ECR Repository

Locate your image repository and proceed to clone the images in AWS: [AWS ECR Console](https://us-east-2.console.aws.amazon.com/ecr/repositories?region=us-east-2)

In the active awsume console, establish a connection:

### Connecting with ECR:

1. Authenticate Docker with AWS ECR:

    ```bash
    aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 553449903150.dkr.ecr.us-east-2.amazonaws.com
    ```

2. Download the Image:

    ```bash
    docker pull 553449903150.dkr.ecr.us-east-2.amazonaws.com/dataintegrator-tf:dev
    ```

    Note: When performing `docker pull`, change the final tag from `latest` to `dev`.

## Uploading to Google Cloud

To upload the connection to Google Cloud, first validate with the command `docker images`. List the downloaded images, in this case corresponding to `8cbdded112a2`, and create a new tag:

```bash
docker tag 8cbdded112a2 us-west1-docker.pkg.dev/troc-cluster-dev/navigator-dev/dataintegrator-tf:dev
```

Then, push the image to your Artifact Registry repository:

```bash
docker push us-west1-docker.pkg.dev/troc-cluster-dev/navigator-dev/dataintegrator-tf:dev
```

### Using the Data Integrator Worker:

Repeat the process for the `dataintegrator-worker` image:

1. Pull the Image from AWS ECR:

    ```bash
    docker pull 553449903150.dkr.ecr.us-east-2.amazonaws.com/dataintegrator-worker-tf:dev
    ```

2. Tag the Image for Google Cloud:

    ```bash
    docker tag 027e72d4613a us-west1-docker.pkg.dev/troc-cluster-dev/navigator-dev/dataintegrator-worker-tf:dev
    ```

3. Push to Artifact Registry:

    ```bash
    docker push us-west1-docker.pkg.dev/troc-cluster-dev/navigator-dev/dataintegrator-worker-tf:dev
    ```
```