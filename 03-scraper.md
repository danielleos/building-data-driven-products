# Scraper setup

**Previous**: [Cosmos DB setup](02-cosmosdb.md) | **Next**: [Data analysis](04-analysis.md)

## Create a VM

Create a virtual machine to run the scraper:
```bash
az vm create --name "danielleos-scraper" \
             --image "UbuntuLTS" \
             --size "Standard_B1s" \
             --generate-ssh-keys \
             --public-ip-address-dns-name "danielleos-scraper"
```

You can list all available sizes using:
```bash
az vm list-sizes --location uksouth --output table
```

## Set up a `conda` virtual environment

1. Log into the VM:
   ```bash
   ssh danielleos-scraper.uksouth.cloudapp.azure.com
   ```
1. Download and install [Miniconda](https://conda.io/miniconda.html):
   ```bash
   wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
   bash Miniconda2-latest-Linux-x86_64.sh -b
   ```
1. Clone this repository from GitHub and move to the scraper folder:
   ```bash
   git clone https://github.com/danielleos/building-data-driven-products.git
   cd building-data-driven-products/ted-scraper
   ```
1. Create a new environment for the scraper:
   ```bash
   ~/miniconda2/bin/conda env create -f environment.yml
   ```

## Set up and start the scraper

1. Activate the environment:
   ```bash
   source ~/miniconda2/bin/activate tedbot
   ```
1. Update the configuration file `tedbot/settings.py` using the values you retrieved during [database setup](02-db-setup.md):

   | Variable            | Value                             |
   | ------------------- | --------------------------------- |
   | `COSMOSDB_ENDPOINT` | Your Cosmos DB endpoint           |
   | `COSMOSDB_KEY`      | Your Cosmos DB `primaryMasterKey` |
1. Start the scraper:
   ```bash
   scrapy crawl ted
   ```
