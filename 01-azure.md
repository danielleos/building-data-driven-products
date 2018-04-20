# Azure setup

**Next**: [Cosmos DB setup](02-cosmosdb.md)

## Set up the Azure CLI

Install the latest version of the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) and [log into your Azure account](https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli).

If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/free) before you begin.

## Select your subscription

You can list your subscriptions using:
```bash
az account list --output table
```

If you have multiple subscriptions, select the one you'd like to use as default:
```bash
az account set --subscription "Azure Internal - London"
```

## Create a resource group

You can list all available locations using:
```bash
az account list-locations --output table
```

Create a resource group in a suitably close location:
```bash
az group create --location uksouth --name "danielleos-data-prod"
```


## Set defaults

Configure the newly created resource group as default:
```bash
az configure --defaults group="danielleos-data-prod"
```
