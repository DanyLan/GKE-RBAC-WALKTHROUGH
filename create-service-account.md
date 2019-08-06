# Create Service Accounts

In order to demonstrate RBAC, three [aliases](https://ahmet.im/blog/kubectl-aliases/) will be created which will be associated with three different accounts. In that way it will be easy to see who is taking action.

1. Admin - this user has full access to all namespaces in the cluster
2. Account1 - this user starts with no access and will be granted increasing levels of access to namespace1.
3. Account2 -this user starts with no access and will be granted increasing levels of access to namespace2.

