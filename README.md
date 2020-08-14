# Deploying a Flask API

This is the project starter repo for the fourth course in the [Udacity Full Stack Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004): Server Deployment, Containerization, and Testing.

In this project you will containerize and deploy a Flask API to a Kubernetes cluster using Docker, AWS EKS, CodePipeline, and CodeBuild.

The Flask app that will be used for this project consists of a simple API with three endpoints:

- `GET '/'`: This is a simple health check, which returns the response 'Healthy'. 
- `POST '/auth'`: This takes a email and password as json arguments and returns a JWT based on a custom secret.
- `GET '/contents'`: This requires a valid JWT, and returns the un-encrpyted contents of that token. 

The app relies on a secret set as the environment variable `JWT_SECRET` to produce a JWT. The built-in Flask server is adequate for local development, but not production, so you will be using the production-ready [Gunicorn](https://gunicorn.org/) server when deploying the app.

## Initial setup
1. Fork this project to your Github account.
2. Locally clone your forked version to begin working on the project.

## Dependencies

- Docker Engine
    - Installation instructions for all OSes can be found [here](https://docs.docker.com/install/).
    - For Mac users, if you have no previous Docker Toolbox installation, you can install Docker Desktop for Mac. If you already have a Docker Toolbox installation, please read [this](https://docs.docker.com/docker-for-mac/docker-toolbox/) before installing.
 - AWS Account
     - You can create an AWS account by signing up [here](https://aws.amazon.com/#).
     
## Project Steps

Completing the project involves several steps:

1. Write a Dockerfile for a simple Flask API
2. Build and test the container locally
3. Create an EKS cluster
4. Store a secret using AWS Parameter Store
5. Create a CodePipeline pipeline triggered by GitHub checkins
6. Create a CodeBuild stage which will build, test, and deploy your code

For more detail about each of these steps, see the project lesson [here](https://classroom.udacity.com/nanodegrees/nd004/parts/1d842ebf-5b10-4749-9e5e-ef28fe98f173/modules/ac13842f-c841-4c1a-b284-b47899f4613d/lessons/becb2dac-c108-4143-8f6c-11b30413e28d/concepts/092cdb35-28f7-4145-b6e6-6278b8dd7527).

## API endpoint

a773ebc52728145d096aa9f305bfecfc-1977917790.us-west-2.elb.amazonaws.com

##References

I used the following sources/pages as reference

1. Managing users or IAM roles for your cluster - https://docs.aws.amazon.com/eks/latest/userguide/add-user-role.html
2. Windows CMD & PowerShell commands - https://www.shellhacks.com/windows-cat-equivalent-cmd-powershell/#:~:text=The%20cat%20command%20in%20Linux,CMD)%20and%20a%20Windows%20PowerShell.
3. Creating an Amazon EKS cluster - https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html
4. AWS CLI command reference - https://docs.aws.amazon.com/cli/latest/reference/

In addition, I used the following github dependecies for solving problems

1. Solution of several questions when I was creating the stack and during the Build step - https://github.com/jungleBadger/FSND-Deploy-Flask-App-to-Kubernetes-Using-EKS/blob/master/troubleshooting/deploy.md
2. Postman collection to test the endpoints - https://github.com/nicholaspretorius/udacity-deployment
