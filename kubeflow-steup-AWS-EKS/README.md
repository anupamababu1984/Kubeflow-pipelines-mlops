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

``export KUBEFLOW_RELEASE_VERSION=v1.7.0``
``export AWS_RELEASE_VERSION=v1.7.0-aws-b1.0.3``
``git clone https://github.com/awslabs/kubeflow-manifests.git && cd kubeflow-manifests``
``git checkout ${AWS_RELEASE_VERSION}``
``git clone --branch ${KUBEFLOW_RELEASE_VERSION} https://github.com/kubeflow/manifests.git upstream
``




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

