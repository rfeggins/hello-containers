# Developers Setup Steps

## Objectives

Before you start, you'll need to set up your environment by installing several CLIs, Docker, and plug-ins and then how to provision a cluster.

## Install required software
You need to install the CLIs to create and manage your Kubernetes clusters in the IBM Cloud Kubernetes Service and to deploy containerized apps.

This section shows you how to install the following CLIs and plug-ins:

- IBM Cloud CLI, Version 0.5.0 or later
- IBM Cloud Container Service plug-in
- IBM Cloud Container Registry plug-in
- Kubernetes CLI, Version 1.7.4 or later
- Docker, Version 1.9. or later

If you already have the CLIs and plug-ins, you can skip the next section.

## Useful Links
IAM https://console.bluemix.net/docs/iam/users_roles.html#userroles
Cloud Foundry Access https://console.bluemix.net/docs/iam/cfaccess.html#cfaccess
Infrastructure Permissions https://console.bluemix.net/docs/iam/infrastructureaccess.html#infrapermission



## Install the IBM Cloud command-line interface (CLI)
1. Install the IBM Cloud command-line interface. After it’s installed, you can access IBM Cloud from your command line with the prefix ibmcloud.

2. Log in to the IBM Cloud CLI: ibmcloud login.
For a federated ID: If you have a federated ID, use ibmcloud login –sso to log in to the IBM Cloud CLI. Enter your user name and use the provided URL in your CLI output to retrieve your one-time passcode.
>
> ibmcloud login --sso
>

## Install the IBM Cloud Container Service plugin
1. Create Kubernetes clusters and manage worker nodes by installing the IBM Cloud Container Service plug-in:
>
> ibmcloud plugin install container-service -r Bluemix
>

Tip: The prefix for running commands by using the IBM Cloud Container Service plug-in is ibmcloud cs.

2. Verify that the plug-in is installed properly:
>
> ibmcloud plugin list
>

The IBM Cloud Container Service plug-in is displayed in the results as container-service.

## Install the IBM Cloud Container Registry plug-in
Use this plug-in to set up your own namespace in a multi-tenant, highly available, and scalable private image registry that is hosted by IBM, and to store and share Docker images with other users.

Docker images are required to deploy containers into a cluster.

Tip: The prefix for running registry commands is ibmcloud cr.

1. Manage a private image repository by installing the IBM Cloud Container Registry plug-in:

>
> ibmcloud plugin install container-registry -r Bluemix
>

2. Verify that the plug-in is installed properly:
>
> ibmcloud plugin list
>
> ibmcloud cr

The plug-in is displayed in the results as container-registry.

Here are some common ""ibmcloud cr" commands
>
>  ibmcloud cr info                          Information about the current IBM Cloud Container Registry command session.
>
>  ibmcloud cr   namespaces         List namespaces for your account.
>
>  ibmcloud cr    images                  List your images in IBM Cloud Container Registry.
>
>  ibmcloud cr    image-inspect      Inspect one or more images in IBM Cloud Container Registry.
>
>  ibmcloud cr   login                       Log the local Docker client in to IBM Cloud Container Registry.
>
>  ibmcloud cr   tokens                    List your registry tokens that are used to access IBM Cloud Container Registry.
>
>  ibmcloud cr    build                      Build a Docker image in IBM Cloud Container Registry.
>
>  ibmcloud cr    region                    Display the targeted region.
>
>  ibmcloud cr    region-set             Set a target region for the IBM Cloud Container Registry commands.

## Install the Docker and Kubernetes CLI (kubectl)

1. To locally build images and push them to your registry namespace, install Docker. The Docker CLI is used to build applications into images.
- https://www.docker.com/products/docker-engine#/download

2. Install the version of kubectl that is the same Kubernetes version for IBM Cloud Container Service.
- https://console.bluemix.net/docs/containers/cs_versions.html#cs_versions

Using an older kubectl with a newer server might produce validation errors.
