# Psitron Kubeflow pipelines 

# Deploy Kubeflow on AWS EKS

## Prerequisites
* **Docker**
Create a Ubuntu environment using Docker. 

* Pull the latest version of the Ubuntu image of your choice.
``docker pull ubuntu:18.04``
* Connect to localhost from your container:
``docker container run -it -p 127.0.0.1:8080:8080 ubuntu:18.04``
* Download the latest package information:
``apt update``
* Install the necessary tools:
``apt install git curl unzip tar make sudo vim wget -y``

## Clone repository
Clone the ``awslabs/kubeflow-manifests`` and the ``kubeflow/manifests`` repositories and check out the release branches of your choosing.

Substitute the value for ``KUBEFLOW_RELEASE_VERSION``(e.g. v1.7.0) and ``AWS_RELEASE_VERSION``(e.g. v1.7.0-aws-b1.0.3) with the tag or branch you want to use below. Read more about releases and versioning if you are unsure about what these values should be.

```
export KUBEFLOW_RELEASE_VERSION=v1.7.0
export AWS_RELEASE_VERSION=v1.7.0-aws-b1.0.3
git clone https://github.com/awslabs/kubeflow-manifests.git && cd kubeflow-manifests
git checkout ${AWS_RELEASE_VERSION}
git clone --branch ${KUBEFLOW_RELEASE_VERSION} https://github.com/kubeflow/manifests.git upstream
```
## Install necessary tools 
Install the necessary tools with the following command:

``make install-tools``

```
#NOTE: If you have other versions of python installed 
#then make sure the default is set to python3.8
alias python=python3.8
```

The `make` command above installs the following tools:

* AWS CLI - A command line tool for interacting with AWS services.
* eksctl - A command line tool for working with EKS clusters.
* kubectl - A command line tool for working with Kubernetes clusters.
* yq - A command line tool for YAML processing. (For Linux environments, use the wget plain binary installation)
* jq - A command line tool for processing JSON.
* kustomize version 5.0.1 - A command line tool to customize Kubernetes objects through a kustomization file.
* python 3.8+ - A programming language used for automated installation scripts.
* pip - A package installer for python.
* terraform - An infrastructure as code tool that lets you develop cloud and on-prem resources.
* helm - A package manager for Kubernetes

## Configure AWS Credentials and Region for Deployment 
To access AWS services, you need an AWS account and setup IAM credentials. Follow AWS CLI Configure Quickstart documentation to setup your IAM credentials.

Your IAM user/role needs the necessary privileges to create and manage your cluster and dependencies. You might want to grant `Administrative Privileges` as it will require access to multiple services.

Run the following command to configure AWS CLI:

```
aws configure --profile=kubeflow
# AWS Access Key ID [None]: <enter access key id>
# AWS Secret Access Key [None]: <enter secret access key>
# Default region name [None]: <AWS region>
# Default output format [None]: json

# Set the AWS_PROFILE variable with the profile above
export AWS_PROFILE=kubeflow

```

Once your configuration is complete, run `aws sts get-caller-identity` to verify that AWS CLI has access to your IAM credentials.





If you want to know in detail about the detailed explanation of how to develop your first kubeflow pipeline, I recommend you take a look at the article: <a href="Kubeflow Pipelines: How to Build your First Kubeflow Pipeline from Scratch"> *Kubeflow Pipelines: How to Build your First Kubeflow Pipeline from Scratch*</a>

<p align="center">
<img src='img/kubeflow.jpg'>
</p>

<!-- files -->
## Files
* **decision_tree**: Contains the files to build the decision_tree component as well as the Dockerfile used to generate the component image.
* **logistic_regression**: Contains the files to build the logistic_regression component as well as the Dockerfile used to generate the component image.
* **download_data**: Contains the files to build the download_data component as well as the Dockerfile used to generate the component image.
* **pipeline.py**: Contains the definition of the pipeline, which when executed generates the ``FirstPipeline.yaml`` file.


<!-- how-to-use -->
## How to use
* It is recommended to have previously installed ``kfp`` as well as configured kubeflow on top of kubernets or a minimal version such as ``minikube`` or AKS or EKS.

<!-- license -->
## License
Distributed under the MIT License. See ``LICENSE.md`` for more information.

