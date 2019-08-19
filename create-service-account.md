# Create Service Accounts

In order to demonstrate RBAC, three [aliases](https://ahmet.im/blog/kubectl-aliases/) will be created which will be associated with three different accounts. In that way it will be easy to see who is taking action.

1. Admin - this user has full access to all namespaces in the cluster
2. Account1 - this user starts with no access and will be granted increasing levels of access to namespace1.
3. Account2 - this user starts with no access and will be granted increasing levels of access to namespace2.

# 1.Create Admin alias

`admin-kubectl` is an alias to `kubectl` that uses the token of the GCP project owner account to authenticate.

    export primary_account="<primary-email-address-of-gcp-project>"
    alias admin-kubectl='kubectl --token="$(gcloud auth print-access-token --account=$primary_account)"'
    
# 2.Create Account1 alias

`account1-kubectl` is an alias to `kubectl` that uses the token associated with service account named `account1` to authenticate. Account name will be in the following format account1@<project_id>.iam.gserviceaccount.com

1. Create account1 service account

       gcloud iam service-accounts create account1
    
2. Capture the full email account

       account1=$(gcloud iam service-accounts list --format='value(email)' --filter='email:account1')
       
   Note:Run the following `gcloud iam service-accounts list --format='value(email)' --filter='email:account1'` in order to check whether account1 returns the appropriate service account.

3. Create a key for service account

       gcloud iam service-accounts keys create key1.json --iam-account $account1 

4. Use the key to activate the service account

       gcloud auth activate-service-account $account1 --key-file=[path_to your_key1.json file]

5. Create account1 alias

       alias account1-kubectl='kubectl --token="$(gcloud auth print-access-token --account=$account1)"'
    
    
