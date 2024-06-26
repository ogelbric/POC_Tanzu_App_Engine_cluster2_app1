# How to add a second cluster to Tanzu Platform
```
Previous articles in this series are: 
  Create cluster with Tanzu Platorm and include in a Space
    https://github.com/ogelbric/POC_Tanzu_App_Engine/blob/main/README.md
  Create first app with Tanzu Platform
     https://github.com/ogelbric/POC_Tanzu_App_Engine_app1/blob/main/README.md
```

## Steps in this doc

```
(1) Create second cluster
(2) Add a label
(3) Create an avaliability target
(4) Change replica count in Space
(5) Change app to tell me which node I am running on (Thank you Matt Benley for the little go app)

```

## (1) Create second cluster

I found running 5 workers as best-effort-medium works best 

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr1.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr2.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr3.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr4.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr5.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr6.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr7.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2cr8.png)

## (2) Add a label

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/label1.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/label2.png)

## (3) Create an avaliability target (actually just a refresh since we have the same label)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2al1.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2al2.png)

![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/cl2al3.png)

## (4) Change replica count in Space

Space before
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp1.png)

Cluster situation before
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp2.png)

Change the replica count
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp3.png)

Things go from red to orange for a while
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp4.png)

Make sure your cluster group goes from red to green 
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp5.png)

Check out the ingress objects for each cluster
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp6.png)

And we have gateways on 2 clusters
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp7.png)

And depending which pod you deployed the URL should be working: 
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp8.png)

And we have 2 clusters in the space and 2 x the app 
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp9.png)

## (5) Change app to tell me which node I am running on (Thank you Matt Benley for the little go app)

```
export KUBECONFIG="/root/.config/tanzu/kube/config"
tanzu plugin install --group vmware-tanzu/app-developer
#
source ~/tanzucli.src
export proj="AMER-East"
export sp="orfspace1"
export org="sa-tanzu-platform"
export cl="orfclustergroup"
export w=''
#export w='--wide'
export line="-----------------------------------------------------------------"
yes | tanzu context delete $org
source ~/tanzucli.src
tanzu login
tanzu project use $proj
tanzu space use $sp 
#
cd orf-nginx-app-engine/
#
tanzu app init
? What is your app's name? orf-nginx-app-engine
? Which directory contains your app's source code? .
? Select container build type to use for this app: buildpacks
✓ Created tanzu.yml
✓ Recorded app configuration to .tanzu/config/orf-nginx-app-engine.yml

#cat /tmp/orf-nginx-app-engine.yml
#apiVersion: apps.tanzu.vmware.com/v1
#kind: ContainerApp
#metadata:
#  creationTimestamp: null
#  name: orf-nginx-app-engine
#spec:
#  image: gcr.io/boreal-rain-256712/go-hostname:latest
#  replicas: 1
#  ports:
#  - name: main
#    port: 8080

cp /tmp/orf-nginx-app-engine.yml .tanzu/config/orf-nginx-app-engine.yml

tanzu build config --build-plan-source-type=ucp --containerapp-registry gcr.io/boreal-rain-256712/{name}
#
#
tanzu deploy
#
```
Node 1:
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp10.png)

Node2
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp11.png)


