#Deploying the 101-aks template

##Create a service principal

```shell
az login
az ad sp create-for-rbac --skip-assignment
```

You will use the output in the template. 
Or you can use the output as variables in an Azure DevOps pipeline.




