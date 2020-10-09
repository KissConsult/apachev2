# Get Apache on IBM Cloud

[IBM Cloud] offers the most open and secure public cloud for business 

## Step 1 provision Kubernetes Cluster

  - Search for **Kubernetes Service** in the search bar
  - Click **Kubernetes Service** from the dropdown menu
  - Choose **classic** or **VPC** 
  - Choose **Geography** (continent)
  - Choose **Single** or **Multizone** 
  - Choose **Worker Zone** (city)
  - Choose a **Worker node setup** or use the preselected one
  - Give cluster a **name** 
  - Click **Create** - it will take approximately 10-20 minutes to provision the cluster

## Step 2 deploy Apache
  
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



 
   [IBM Cloud]: <http://cloud.ibm.com>
   [Resources]: <http://cloud.ibm.com/resources>
