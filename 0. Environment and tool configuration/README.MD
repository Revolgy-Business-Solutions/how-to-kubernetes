# Environment and tool configuration

In this mini lesson we will prepare some tools and environments that we will need thoughout all the lessons. We will be leveraging some benefits of hosting Kubernetes. In this case our provider will be Google Cloud Platform (GCP). In case you will be using some other options (Amazon - EKS, Microsoft - AKS, self-hosted kubernetes - minikube etc.) you will need to adjust some steps acordingly. That will not be part of the lessons but we will try to point every GCP binded steps throughout the courses.

## CLI tools initiation

In these courses we will use following cli tools:

- gcloud (GCP CLI tool - use different tools acording to your kubernetes environment, or non in case of self hosting kubernetes)
- kubectl (kubernetes CLI)
- docker

### gcloud

Download: [cloud.google.com/sdk/install](https://cloud.google.com/sdk/install)

Init configuration: `gcloud init`

Gcloud init will guide you through init configuration including authenticating with your gmail account which we will use to create our GCP project. Gmail account is a requirement for hosting Kubernets on GCP, if you don't have gmail account, create one at for purposes of this courses.

### kubectl

Kubernetes cli can be installed via terminal as a gcloud component. In can be installed as a standalone app in case you won't be using GCP infrustructure but considering we will be working on GCP infrastructure it is not advisable.

```
gcloud components install kubectl
```

I case of installing standalone version of kubectl, follow instructions acording to your OS (distro) here: `https://kubernetes.io/docs/tasks/tools/install-kubectl/` 

*DISCLAIMER:* Choosing self-hosted version of kubernetes is not advised for beginners since it brings additional operations such as managing kubernetes master, internal kubernetes application etc. Hosted version such as GKE (Google Kubernetes Engine) on GCP allows to learn kubernetes practices without the extra overhead.

### Docker

Docker can be ususally installed via package manager in case of linux distributions and by downloading installer in case of Windows and Mac OS. Please follow instruction acording to your OS and distribution here: [docs.docker.com/install](https://docs.docker.com/install)

### Tool Check

Check that all tools needed are installed correctly by running this commands

```
gcloud version
kubectl version
docker version
```

You should see outcome similar to this:

```
>> gcloud version

Google Cloud SDK 210.0.0
alpha 2018.07.16
app-engine-go 
app-engine-python 1.9.73
beta 2018.07.16
bq 2.0.34
core 2018.07.27
gsutil 4.33
kubectl 

>> kubectl version

Client Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.7", GitCommit:"0c38c362511b20a098d7cd855f1314dad92c2780", GitTreeState:"clean", BuildDate:"2018-08-20T10:09:03Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"10+", GitVersion:"v1.10.7-gke.6", GitCommit:"06898a4d0f2b96f82b43d9e59fa2825bd3d616a2", GitTreeState:"clean", BuildDate:"2018-10-02T17:32:01Z", GoVersion:"go1.9.3b4", Compiler:"gc", Platform:"linux/amd64"}

>> docker version
Client:
 Version:           18.06.0-ce
 API version:       1.38
 Go version:        go1.10.3
 Git commit:        0ffa8257ec
 Built:             Sun Aug 19 09:47:50 2018
 OS/Arch:           linux/amd64
 Experimental:      false

Server:
 Engine:
  Version:          18.06.0-ce
  API version:      1.38 (minimum version 1.12)
  Go version:       go1.10.3
  Git commit:       0ffa8257ec
  Built:            Sun Aug 19 09:47:31 2018
  OS/Arch:          linux/amd64
  Experimental:     false
```

If you don't see the server part of the output, it's not wrong, you didn't connect your CLI nowhere yet. 

## GCP Environment preparation

As mentioned we will be using GCP and its hosted kubernetes called Google Kubernetes Engine. For this we will need a gmail account and GCP project created with billing enabled.

NOTE: Interface of GCP console changes quite often, there is a possibility that some steps in our instruction will not be quite accurate. It is usualy a matter of repositioning of information and steps, naming usualy stay the same, so adjust process acordingly. If you get stuck or want to point some inconsistencies, write us, we will be happy to help you or adjust instructions acordingly!

### Project creation

At [console.cloud.google.com](https://console.cloud.google.com) at the top there is option to "Select a project" where you can crate a "New project". Here you have to only fill name of your new project that will automatically generate a project ID

### Enabling billing

In order to use GCP features including Kubernetes, we need to have billing enabled. This include providing you credit card information. Note that *New users of GCP console have $300 (12 months) trial credit and no fees are applied to your credit card unless you manualy upgrade your cluster from trial stage*. All of our courses are designed to fit into this trial account. If it would happend that you run out of free credit, your services will be shut down until you manualy upgrade your account, no fees are aplied until then. You can allways create new Gmail account with new GCP project.

### Creating kubernetes cluster

## Authenticating into kubernetes cluster