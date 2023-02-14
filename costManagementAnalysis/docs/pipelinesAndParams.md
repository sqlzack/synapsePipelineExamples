## Pipeline and Parameter Explanation


## Parameter Definition.
- **SubscriptionId** - The Azure SubscriptionId from which Synapse will pull Cost Management Data. This can be [found](https://learn.microsoft.com/en-us/azure/azure-portal/get-subscription-tenant-id#find-your-azure-subscription) in the Overview page of the Subscription in the Azure Portal.
- **exportName** - Name that will show up in the Exports section of Cost Management when running these Synapse Pipelines. It does not have to be pre-created but it should not conflict with anything already in existence.
- **storageAccountContainerName** - The Blob Container in the Storage Account where you'll be storing the Exports from Cost Management in CSV format before they go into Parquet/Delta.
- **rootFolderPath** - This is the root path inside the Storage Account Container where the CSV Exports will reside. I used "raw/costManagementExport" (no quotes).
- **storageResourceGroupName** -  Resource Group the Cost Management Export Storage Account belongs to.
- **storageAccountName** - Name of the Storage Account that will hold the raw CSV Exports from Cost Management.
- **monthsOfHistory** - Integer value representing the months of history to export from Cost Management. 0 represents the currrent month, 1 represents the previous month, and so forth.
- **destinationRootPath** - The root path inside the Storage Account that will hold the parquet or delta files. I used "enriched/costManagementParqet" or "enriched/costManagementDelta".
- **synapseWorkspaceName** - The name of the Synapse Workspace containing the Serverless SQL pool and database containing the views exposing the parquet or delta files.
- **costManagementDbName** - The name of the Synapse Serverless SQL Database containing the views exposing the parquet or delta files.
- **destinationStorageAccountName** - Name of the Storage Account that will hold the parquet or delta files that are created as a result of the pipelines.
- **destinationStorageAccountContainerName** - The blob container inside the destination storage account that will hold the delta or parquet files created by the pipelines.

### Explanation and Pipeline Definition - WIP
Now that all artifacts are deployed to run and load the exports, we'll dive in to what each peice does.

1) The Linked Services were deployed as fully parameterized. That means no service names saved in source code and also means that these values can be defined when creating triggers. Beyond portability and obfuscation there are more virtues of doing this explained [here](https://learn.microsoft.com/en-us/azure/data-factory/parameterize-linked-services?tabs=data-factory).
2) The pipelines, datasets, and data flows deployed through templates are also parameterized. Partially to allow Linked Services to be parameterized but also to pull dynamic values like a list of historical months or set the output format between Parquet and Delta. 
