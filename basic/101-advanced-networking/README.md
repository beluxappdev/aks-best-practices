# Deploying the advanced-networking-aks template

## Create a service principal

```shell
az login
az ad sp create-for-rbac --skip-assignment

az ad sp show --id <appID> --query objectId
```

You will use the output in the template. 
Or you can use the output as variables in an Azure DevOps pipeline.

## Create a resource group

```shell
az group create -n demo-aks-network -l westeurope
```

You will also need the role assignments

```shell
VNET_ID=$(az network vnet show --resource-group demo-aks-network --name VNet1 --query id -o tsv)
SUBNET_ID=$(az network vnet subnet show --resource-group demo-aks-network --vnet-name VNet1 --name Subnet1 --query id -o tsv)

az role assignment create --assignee <appId> --scope $VNET_ID --role Contributor
```



## Deploy through Azure Devops

Copy paste output from az ad sp create command into 2 new pipeline variables called ServicePrincipalId and ServicePrincipalKey. 
Run azure-pipelines.yml as pipeline.

