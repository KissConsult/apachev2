# Get Apache on IBM Cloud

[IBM Cloud] offers the most open and secure public cloud for business . You should have an IBM Cloud account, otherwise you can [register here].
At the end of the tutorial you will have a cluster with an Apache up and runnning.

1. We will provision a new Kubernetes Cluster for you if ,you already have one skip to step **2**
2. We will deploy  the IBM Cloud Block Storage plug-in ,if already have it skip to step **3**
3. Apache deployment 

## Step 1 provision Kubernetes Cluster

* Click the **Catalog** button on the top 
* Select **Service** from the catalog
* Search for **Kubernetes Service** and click on it
![Kubernetes](/kubernetes-select.png)
* You are now at the Kubernetes deployment page ,you need to specify some details about the cluster 
* Choose a plan **standard** or **free** , the free plan only has one worker node and no subnet , to provision a standard cluster , you will need to upgrade you account to Pay-As-You-Go 
  *To upgrade to a Pay-As-You-Go account, complete the following steps:

  * In the console, go to Manage > Account.
  * Select Account settings, and click Add credit card.
  * Enter your payment information, click Next, and submit your information
* Choose **classic** or **VPC** , read the [docs] and choose the most suitable type for yourself 
 ![VPC](/infra-select.png)
* Now choose your location settings , for more information please visit [Locations]
  * Choose **Geography** (continent)
![continent](/location-geo.png)
  * Choose **Single** or **Multizone** , in single zone your data is only kept in on datacenter , on the other hand with Multizone it is distributed to multiple zones , thus  safer in an unforseen zone failure 
![avail](/location-avail.png)
  * Choose a **Worker Zone** if using Single zones or **Metro** if Multizone
 ![worker](/location-worker.png) 
    * If you wish to use Multizone please set up your account with [VRF] or [enable Vlan spanning]
 
* Choose a **Worker node setup** or use the preselected one , set **Worker node amount per zone**
![worker-pool](/worker-pool.png)
* Give cluster a **name** then click **Create** - it will take approximately 10-20 minutes to provision the cluster
![create](/create.png)
* Wait for you cluster do be provisioned 
![cluster-prepare](/cluster-prepare.png)
* Your cluster is ready for usage 
![cluster-ready](/cluster-done.png)

## Step 2 deploy IBM Cloud Block Storage plug-in
The Block Storage plug-in is a persistent, high-performance iSCSI storage that you can add to your apps by using Kubernetes Persistent Volumes (PVs).
 
* Click the **Catalog** button on the top 
* Select **Software** from the catalog
* Search for **IBM Cloud Block Storage plug-in** and click on it
![Block](/block-search.png)

* On the application page Click in the _dot_ next to the cluster , you wish to use
* Click on  **Enter or Select Namespace** and choose the default Namespace or use a custom one 
![block-c](/block-cluster.png)
* Give a **name** to this workspace 
* Click **install** and wait for the deployment
![block-create](/block-storage-create)
 

## Step 3 deploy Apache
  
We will deploy  Apache on our cluster 
  
* Click the **Catalog** button on the top 
* Select **Software** from the catalog
* Search for **Apache** and click on it
![Apache](/apache-select.png)


* On the application page Click in the _dot_ next to the cluster , you wish to use
![Cluster](/cluster-select.png)
* Click on  **Enter or Select Namespace** and choose the default Namespace or use a custom one 
![Namespace](/namespace.png)
* Give a unique **name** to workspace , which you can easily recognize
![Name](/name.png)
* After finishing everything , **tick** the box next to the agreements and click **install**
![Install](/install.png)

## Verify Apache installation

* Go to [Resources] in your browser 
* Click on **Clusters**
* Click on your Cluster
![Resourcelect](/resource-select.png)

* Now you are at you clusters overview ,here Click on **Actions** and **Web terminal** from the dropdown menu
![Actions](/cluster-main.png)
* Click **install** - wait couple of minutes 
* Click on **Actions**
* Click **Web terminal** --> a terminal will open up

* **Type** in the terminal:
 ```sh
$ kubectl get service --all-namespaces
```
![kubectl](/kubectl.png)
* Running Apache service will be visible 
* Copy the **External ip** , you can access the website on this IP
* Paste it into your browser
* Apache welcome message will be visible

![works](/apache-works.png)

You successfully deployed an Apache webserver on IBM Cloud ! 



 
   [IBM Cloud]: <http://cloud.ibm.com>
   [Resources]: <http://cloud.ibm.com/resources>
   [Register Here]: <http://cloud.ibm.com/registration>
   [docs]: <https://cloud.ibm.com/docs/containers?topic=containers-infrastructure_providers>
   [Locations]: <https://cloud.ibm.com/docs/containers?topic=containers-regions-and-zones#zones>
   [VRF]: <https://cloud.ibm.com/docs/dl?topic=dl-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud>
   [enable Vlan spanning]: <https://cloud.ibm.com/docs/vlans?topic=vlans-vlan-spanning#vlan-spanning>
