# GKE-RBAC-WALKTHROUGH

While Cloud IAM is a good first level of security for GKE, Role-Based Access Control can offer a higher degree of granularity. Different teams might need different sort of access when managing an app on GKE. For instance, a team developers will require a different type of access to a team of testers. That type of finer control can be achieved through RBAC which will allow you to secure your namespaces as well as your clusters.

# WALKTHROUGH

1. [Create a new cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/creating-a-cluster) and connect to it.
2. [Create aliases for admin account and two service accounts](https://github.com/DanyLan/GKE-RBAC-WALKTHROUGH/blob/master/create-service-account.md).
3. [Create two namespaces](https://github.com/DanyLan/GKE-RBAC-WALKTHROUGH/blob/master/namespaces.md).
4. [Create roles and rolebindings](https://github.com/DanyLan/GKE-RBAC-WALKTHROUGH/blob/master/create-roles.md).
5. [Create cluster roles and cluster rolebindngs](https://github.com/DanyLan/GKE-RBAC-WALKTHROUGH/blob/master/create-cluster-roles.md).
