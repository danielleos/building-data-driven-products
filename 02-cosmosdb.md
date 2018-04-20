# Cosmos DB setup

**Previous**: [Azure setup](01-azure.md) | **Next**: [Scraper setup](03-scraper.md)

## Create resources

1. Create a Cosmos DB account:
   ```bash
   az cosmosdb create --name "danielleos-cosmosdb"
   ```
1. Create a database within the account:
   ```bash
   az cosmosdb database create --db-name "ted" \
                               --name "danielleos-cosmosdb" \
                               --resource-group-name "danielleos-data-prod"
   ```

## Retrieve credentials

1. Retrieve your Cosmos DB endpoint and keys:
   ```bash
   az cosmosdb list --output table
   ```
1. Retrieve your Cosmos DB keys:
   ```bash
   az cosmosdb list-keys --name "danielleos-cosmosdb"
   ```
