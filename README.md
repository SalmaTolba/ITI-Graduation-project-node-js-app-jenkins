# Graduation-Project-ITI

## ssh vm instance

```bash
gcloud compute ssh bastion-vm --project salma-358017 --zone us-central1-a -- -L8888:127.0.0.1:8888
```

## Install kubctl

![Screenshot from 2022-08-03 07-08-42.png](images/Screenshot_from_2022-08-03_07-08-42.png)

## then connect to the cluster (GKE)

```bash
gcloud container clusters get-credentials gke-cluster --zone us-central1-a --project salma-358017
```

### Install docker

![Screenshot from 2022-08-03 07-07-31.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_07-07-31.png)

### Install git

![Screenshot from 2022-08-03 07-09-32.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_07-09-32.png)

### Install gcloud

![Screenshot from 2022-08-03 07-09-23.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_07-09-23.png)

### Install open-jdk

To connect the slave in jenkins with cloud vm-instance 

![Screenshot from 2022-08-03 07-07-07.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_07-07-07.png)

### Build docker image for Jenkins

![Screenshot from 2022-08-03 05-53-14.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_05-53-14.png)

![Screenshot from 2022-08-03 05-53-41.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_05-53-41.png)

![Screenshot from 2022-08-03 05-54-05.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_05-54-05.png)

![Screenshot from 2022-08-03 05-57-54.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_05-57-54.png)

### Create namespace then deploy Jenkins

```bash
kubectl create namespace jenkins-ns1
kubectl config set-context --current –namespace=jenkins-ns1
kubectl create -f deployment.yaml
kubectl create -f serviceLB.yaml
```

![Screenshot from 2022-08-03 06-01-05.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-01-05.png)

![Screenshot from 2022-08-03 06-09-32.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-09-32.png)

**Jenkins link : [http://35.202.111.14:8080](http://35.202.111.14:8080/)**

![Screenshot from 2022-08-03 06-13-05.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-13-05.png)

## create credentials for dockerhub

![Screenshot from 2022-08-03 06-17-03.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-17-03.png)

## Create credentials for slave

Generate key in cloud vm-instane , put the public key in the authorized_keys file and the private on in the credential configurations

-username of instance to ssh

![Screenshot from 2022-08-03 06-28-30.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-28-30.png)

-private key generated from ssh-keygen

![Screenshot from 2022-08-03 06-28-42.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-28-42.png)

Here the credentials created

![Screenshot from 2022-08-03 06-29-04.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-29-04.png)

## Let’s create slave

![Screenshot from 2022-08-03 06-36-32.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-36-32.png)

![Screenshot from 2022-08-03 06-36-47.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-36-47.png)

![Screenshot from 2022-08-03 06-36-59.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-36-59.png)

![Screenshot from 2022-08-03 06-37-15.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-37-15.png)

![Screenshot from 2022-08-03 06-36-06.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-36-06.png)

## Build pipeline that pull docker file from git then build the image of the application then push it to dockerhub then deploy the application

![Screenshot from 2022-08-03 06-47-51.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-47-51.png)

![Screenshot from 2022-08-03 06-48-02.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-48-02.png)

![Screenshot from 2022-08-03 06-50-03.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-50-03.png)

![Image pushed successfully](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-58-04.png)

Image pushed successfully

**Pipline automated successfully**

## Get IP:Port for the application

![Screenshot from 2022-08-03 06-54-00.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-54-00.png)

## OR

![Screenshot from 2022-08-03 06-52-20.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-52-20.png)

# Finallyyyyyy

## App link: [http://34.68.90.32:3000/](http://34.68.90.32:3000/)

![Screenshot from 2022-08-03 06-56-18.png](Graduation-Project-ITI%20e783fb43d83645f4ac77e8a6fcfef9f0/Screenshot_from_2022-08-03_06-56-18.png)