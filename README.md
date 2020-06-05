# CircleCI 2.0 Demo
Simple Node.js project to demonstrate CircleCI capabilities.

## Prerequisites
- [Yarn](https://yarnpkg.com/) and [Node.js](https://nodejs.org/en/).
- [DockerHub](https://hub.docker.com/) repository for an image.
- [AWS Account, Access, and Secret Keys](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)
- [AWS ECR](https://aws.amazon.com/ecr/) repository for an image.
- A [context](https://circleci.com/docs/2.0/contexts/) named `demo-prod` with the following ENV variables defined:

Variable Name         | Description 
----------------------|----------------------------------------------------
AWS_ACCESS_KEY_ID     | AWS Access Key ID
AWS_SECRET_ACCESS_KEY | The AWS Secret Key generated with the Access Key ID
AWS_S3_BUCKET_NAME    | URI of bucket name in the form of "s3://bucket-name"
AWS_REGION            | Same value as AWS_DEFAULT_REGION
AWS_ECR_ACCOUNT_URL   | URL to the account's ECR, without the repo name (ends in ".com")
AWS_ECR_REPO_NAME     | Name of the repository (e.g "my-image-repo"). `AWS_ECR_ACCOUNT_URL` combines with `AWS_ECR_REPO_NAME` to form the full AWS ECR tag.
DOCKER_LOGIN          | Username for DockerHub login
DOCKER_PWD            | Password to the DockerHub login
DOCKER_TAG            | Full tag for the DockerHub repository (e.g. `username/repo`)

## Setup & Run
1. Clone the repository and run `yarn` to install dependencies.
2. Run `yarn start` to start a simple web server serving the static assets.

## Test
The test uses [TestCafe](https://devexpress.github.io/testcafe/) to run UI tests. It also assumes Chrome and Firefox browsers available on the system.

1. Run `yarn test` to start tests.

## Deploy
[CircleCI](https://circleci.com/) is used to automatically run the tests and, upon manual approval, build Docker images, push them to DockerHub & ECR, and then deploy the website files to S3.

