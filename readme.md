# Sample Node.js Project

A Node.js project written using Express. EJS was used as the view engine.

# Installation

You need to write the following commands on the terminal screen so that you can run the project locally.

```sh
1. git clone git@github.com:acemilyalcin/sample-node-project.git
2. cd sample-node-project
3. npm install
4. npm start
```

The application is running on [localhost](http://localhost:3000).

# Sample Node.js Project

A Node.js project written using Express. EJS was used as the view engine.

---

## CI/CD Pipeline with GitHub Actions

This project includes a GitHub Actions workflow (`ci.yml`) to automate the build and deployment process. The workflow performs the following tasks:
1. **Checkout Code**: Pulls the latest code from the repository.
2. **Set Up Docker**: Configures Docker Buildx for building images.
3. **Push to DockerHub**: Builds and pushes the Docker image to DockerHub.
4. **Push to AWS ECR**: Builds and pushes the Docker image to AWS Elastic Container Registry (ECR).

### Setting Up the Workflow

1. **Add the Workflow File**  
   The workflow file is located at `.github/workflows/ci.yml`. Ensure it is added to your repository.

2. **Configure GitHub Secrets**  
   Add the following secrets to your GitHub repository under **Settings > Secrets and variables > Actions**:
   - `DOCKERHUB_USERNAME`: Your DockerHub username.
   - `DOCKERHUB_PASSWORD`: Your DockerHub password or personal access token.
   - `AWS_ACCESS_KEY_ID`: Your AWS access key ID.
   - `AWS_SECRET_ACCESS_KEY`: Your AWS secret access key.
   - `AWS_REGION`: The AWS region where your ECR repository is located (e.g., `us-east-1`).
   - `AWS_ACCOUNT_ID`: Your AWS account ID.

3. **Create an ECR Repository**  
   Ensure an ECR repository named `sample-node-project` exists in your AWS account. You can create it via the AWS Management Console or CLI.

4. **Trigger the Workflow**  
   The workflow runs automatically on:
   - Pushes to the `main` branch.
   - Pull requests targeting the `main` branch.

   You can also manually trigger the workflow from the **Actions** tab in your GitHub repository.

---

## Running the Application Locally

Follow these steps to run the project locally:

### Prerequisites
- [Node.js](https://nodejs.org/) installed on your machine.
- [Docker](https://www.docker.com/) installed if you want to run the app in a container.

### Installation

Run the following commands in your terminal:

```sh
# Clone the repository
git clone git@github.com:acemilyalcin/sample-node-project.git

# Navigate to the project directory
cd sample-node-project

# Install dependencies
npm install

# Start the application
npm start
```

The application will be running on [http://localhost:3000](http://localhost:3000).

---

## Running the Application with Docker

To run the application using Docker:

1. Build the Docker image:
   ```sh
   docker build -t sample-node-project .
   ```

2. Run the Docker container:
   ```sh
   docker run -p 3000:3000 sample-node-project
   ```

The application will be accessible at [http://localhost:3000](http://localhost:3000).

---

## Deployment

The CI/CD pipeline automatically builds and pushes the Docker image to:
- **DockerHub**: `${{ secrets.DOCKERHUB_USERNAME }}/sample-node-project:latest`
- **AWS ECR**: `<AWS_ACCOUNT_ID>.dkr.ecr.<AWS_REGION>.amazonaws.com/sample-node-project:latest`

Ensure your AWS ECR repository and DockerHub account are properly configured to receive the images.
