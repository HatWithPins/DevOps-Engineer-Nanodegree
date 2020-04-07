# DevOps Engineer Nanodegree Capstone

For my capstone, I'm deploying a simple Nginx server that serves a simple page with my name and a background color (blue or green).

The folders and their purpouse are:
1. **CloudFormation**: stores the template in YAML format and the parameters in JSON. The template deploys a VPC in two avilability zones with a public and private subnets which communicates between them through a gateway. The template also deploys an EKS cluster with the nodes, a jumpbox and the Jenkins server. The Jenkins server runs some commands in order to install the neccesary dependencies and setting the correct permissions in order to allow Jenkins to use Docker and the last version (1.18) of the AWS CLI. Even so, is neccesary to do some manual work configuring AWS CLI and mapping the associated user to the user map in EKS.
2. **Blue** and **Green**: those two are the blue and green deployment (surprise!). Each one contains a Dockerfile, an index.html and the controller for kubectl.

The last two files are the Jenkinsfile and a configuration JSON for kubectl. Jenkinsfile contains the pipeline stages and steps: linting both dockerfiles, building the images, pushing and deploying in the kubernetes cluster. blue-green-service.json expose the blue or green applications through a load balancer, it includes an app selector.
