## Export and Analyze Cost Management Data with Synapse Pipelines and Serverless SQL

This is a proof of concept to use the Cost Managment Export REST API endpoints, Synapse Pipelines, and Synapse Serverless SQL Pools to customize the analysis of Azure Cost Management data. Once the pipelines have completed you have the option of querying the resulting partitioned Parquet or Delta tables by using views that are created by the process and surfaced in a Serverless SQL Database. These views could be used to explore existing data, combine with other data sources, or as a base for reporting in Power BI.

**IMPORTANT NOTE**
The context of this solution is the _Subscription_. In an enterprise there will be several subscriptions so you will need to employ one of a few options. The best option would be to create exports at the Enrolllment scope. Another option would be to create a supporting Synapse Pipeline that accepts a list of SubscriptionIds and then loops through them running the 00_costMgmtMaster pipeline in this Proof of concept.

## Pre-Requisites

1) A Synapse Workspace that has [Cost Management Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#cost-management-contributor) and [Monitoring Reader](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#monitoring-reader) RBAC access on the Subscription(s) containing the Cost Managment data to be exported.
2) Storage Blob Contributor access granted for the [Synapse Workspace Managed Identity](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#monitoring-reader) on source and destination Storage Accounts.

## Steps to Create Pipelines/Database
1) [Add Linked Services to Synapse Workspace](./docs/linkedServices.md)
2) Add Pipelines from the included template. 
3) **OPTIONAL: Only if writing to Delta.** [Create an Azure Integration Runtime to support Data Flows](./docs/integrationRuntime.md)
4) [Pipeline and Parameter Explanation](./docs/pipelinesAndParams.md)
5) [Run or Trigger the Pipelines](https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers#create-triggers-with-ui)