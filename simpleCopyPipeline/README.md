## Simple Data Lake to Data Lake Copy Pipeline
This pipeline is meant to provide an example of a simple parameter-driven Linked Service, Dataset, and Pipeline for Synapse Pipelines. It will copy a specified file from one Data Lake source to a Data Lake destination and maintain the file's original format by using a [binary-formatted dataset](https://learn.microsoft.com/en-us/azure/data-factory/format-binary) and a pipeline using [Copy Activity](https://learn.microsoft.com/en-us/azure/data-factory/copy-activity-overview). This could be used with a metadata-driven process, inside of loops, or through other means to acheive ingestion from other domains containing data in Azure Data Lake.

## Set up in Synapse Workspace
1) Import the ls_datalake linked service by following the steps in this [guide](https://github.com/sqlzack/synapsePipelineExamples/blob/main/costManagementAnalysis/docs/linkedServices.md).
2) Import the [pl_copyData_adls2adls template](./code/linkedService/../pipeline/pl_copyData_adls2adls.zip) from this repo by following the steps outlined in this [guide](https://github.com/sqlzack/synapsePipelineExamples/blob/main/costManagementAnalysis/docs/createPipelines.md).
3) Publish and Trigger or Debug the pipeline. When prompted, refer the the parameters below and fill out accordingly.

## Parameter Definition.
- **sourceStorageAccountName** - Name of the Storage Account where the source files reside.
- **sourceStorageContainerName** - The Blob Container in the Storage Account where the source files reside.
- **sourceStorageRootPath** - This is the root path inside the Storage Account Container where the source files reside.
- **sourceStorageFileName** - The source file name inside the Storage Account, Container, and Root Path.
- **destStorageAccountName** - Name of the Storage Account where to transfer the destination files.
- **destStorageContainerName** - The Blob Container in the Storage Account where the destination files will be transferred.
- **destStorageRootPath** - This is the root path inside the Storage Account Container where the destination files will be transferred.
- **destStorageFileName** - The destination file name inside the Storage Account, Container, and Root Path.
