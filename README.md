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

## (5) change app to tell me which hode I am running on 

Node 1:
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp10.png)

Node2
![Version](https://github.com/ogelbric/POC_Tanzu_App_Engine_cluster2_app1/blob/main/sp11.png)


