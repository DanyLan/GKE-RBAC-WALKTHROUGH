# Creating roles

We are going to give permission for account1 to list pods in namespace1.

1. Use the `admin-kubectl` user to install an nginx pod in namespace1

       admin-kubectl run nginx --image=nginx --namespace=namespace1
       
2. Test with the following two commands. `admin-kubectl` will work as expected while `account1-kubectl` should fail.

       admin-kubectl get pod --namespace=namespace1
       account1-kubectl get pod --namespace=namespace1
       
3. Create a role that will allow account1 to list pods

       admin-kubectl create role pod-reader \
           --verb=get \
           --verb=list \
           --verb=watch \
           --resource=pods \
           --namespace=namespace1
           
To view role: admin-kubeclt describe roles pod-reader --namespace=namespace1

4. Create a role bindng to associate role `pod-reader` to acccount1.

       admin-kubectl create rolebinding account1-pod-reader-binding \
           --role=pod-reader \
           --user=$account1 \
           --namespace=namespace1
           
5. Try again

       account1-kubectl get pods --namespace=namespace1
