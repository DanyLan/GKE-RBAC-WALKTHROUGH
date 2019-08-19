# Creating roles

We are going to give permission for account1 to list pods in namespace1.

1. Use the `admin-kubectl` user to install an nginx pod in namespace1
    admin-kubectl run nginx --image=nginx --namespace=namespace1
