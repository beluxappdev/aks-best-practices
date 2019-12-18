# Deploying the 101-aks template

## Create a service principal

```shell
az login
az ad sp create-for-rbac --skip-assignment
```

You will use the output in the template. 
Or you can use the output as variables in an Azure DevOps pipeline.

## Create a resource group

```shell
az group create -n demo-aks-101 -l westeurope
```


## Deploy through Azure Devops

Copy paste output from az ad sp create command into 2 new pipeline variables called ServicePrincipalId and ServicePrincipalKey. 
Run azure-pipelines.yml as pipeline.

