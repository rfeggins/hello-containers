#  Provision a cluster
Before you dive into Kubernetes, you need to provision a cluster for your containerized app. Then, you won’t need to wait for it to be ready for the labs in this course. A cluster is a set of resources, worker nodes, networks, and storage devices that keep apps highly available. After you have your cluster, then you can deploy your apps in containers.

Be sure you installed the CLIs as described previously.

Provisioning a cluster can take a few minutes.

Go to the IBM Cloud catalog and provision a Kubernetes cluster.
Enter a cluster name. Free clusters are deployed in the region that you select, but you cannot choose the location (data center).
Click Create Cluster.

The worker node in the cluster takes a few minutes to provision. You can see the status of the worker node in the Worker nodes tab. When the status reaches Ready, your worker node is ready to be used.

## Push an image to IBM Cloud Container Registry
You use the IBM Cloud Container Registry to push or pull an image.

1. Clone or download the GitHub repository associated with this course.
2. Change directory to Lab 1:

cd "Lab 1"

3. Log in to the IBM Cloud CLI. To specify an IBM Cloud region, include the API endpoint.

If you have a federated ID, use ibmcloud login --sso to log in to the IBM Cloud CLI. You know you have a federated ID if the login fails without the --sso and succeeds with the --sso option.
>
> ibmcloud login
>

4. Run ibmcloud cr login and log in with your IBM Cloud credentials. This will allow you to push images to the IBM Cloud Container Registry.

Tip: The commands in this lab show the ng region. Replace ng with the region outputted from the ibmcloud cr login command.

5. Upload images to the IBM Cloud Container Registry by creating a namespace:
>
> ibmcloud cr namespace-add <my_namespace>
>

6. Build the example Docker image:

docker build --tag registry.ng.bluemix.net/<my_namespace>/hello-world .

7. Verify the image is built:

docker images

8. Push that image to IBM Cloud Container Registry:

docker push registry.ng.bluemix.net/<namespace>/hello-world

9. Make sure that the cluster you created previously is ready to use:
  - Run ibmcloud cs clusters and make sure that your cluster is in Normal state.
  - Run ibmcloud cs workers <yourclustername> and make sure that all workers are in Normal state with a Ready status.
  - Make a note of the public IP of the worker.
  
You are now ready to use Kubernetes to deploy the hello-world application.
