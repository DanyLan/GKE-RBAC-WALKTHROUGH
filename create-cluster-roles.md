# Create Cluster Roles

We are going to give permission for account1 to list deployments in all namespaces, that is across the whole cluster.

1. Use the `admin-kubeclt` user to install an nginx pod in namespace2. Keep in mind there is already a deployment/pod in namespace1

       admin-kubectl run nginx --image=nginx --namespace=namespace2
       
2. Test will the following commands. `admin-kubectl` will work as expected while `account1-kubectl` should fail.

       admin-kubectl get deployments --namespace=namespace1
       admin-kubectl get deployments --namespace=namespace2

       account1-kubectl get deployments --namespace=namespace1
       account1-kubectl get deployments --namespace=namespace2
       
3. Create a cluster role that contains the necessary permissions

       admin-kubectl create clusterrole deployment-reader \
           --verb=get \
           --verb=list \
           --verb=watch \
           --resource=deployments

4. Create a cluster role binding to associate cluster role `deployment-reader` to account1

       admin-kubectl create clusterrolebinding account1-deployment-reader-binding \
           --clusterrole=deployment-reader \
           --user=$account1
 
5. Try again

       account1-kubectl get deployments --namespace=namespace1
       account1-kubectl get deployments --namespace=namespace2
