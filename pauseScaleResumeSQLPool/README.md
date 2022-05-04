## Pause Scale Resume Synapse Dedicated SQL Pool

![](./image/pl_pauseScaleResume.png)

The pl_pauseScaleResume pipeline can be used to manage Synapse Analytics Dedicated SQL Pools. All necessary paramaters are included to perform this process. The only pre-requisite is ensuring the Managed Identity for your Synapse Workspace has Contributor access to the Dedicated SQL Pool.

## Optional Pipeline - All Pools Resume/Pause

![](./image/pl_allPoolsResumeOrPause.png)

The pl_allPoolsResumeOrPause is meant to automatically take the Action set in parameters on all Dedicated SQL pools in your Synapse Workspace. This could be handy in development environments. Remember if you scale up using this pipeline that all pools in your environment will scale as well. It is reccommended to scale up using the pl_pauseScaleResume pipeline.

## Parameters
 - Action - Action you are wanting to take against the dedicated pool. Accepts the values of pause, resume, or scale.
 - ActionScale - Only used when the Action parameter is set to scale. Accepts values from DW100c to DW30000c
 - SubscriptionId - SubscriptionId where the Synapse workspace resides.
 - ResourceGroup - Resource group where the Synapse workspace resides.
 - SynapseWorkspace - Name of the Synapse Workspace the dedicated pool resides in.
 - SqlPool - Name of the Dedicated Pool to pause, resume, or scale.
 - Region - Only used with the Action parameter is set to scale.The Azure region the SqlPool parameter resides in. 
 - EmptyBodyForPost - This is meant to get around Synapse Pipelines requirements for a body on POST and PUT methods. The only value it should be set to is {} as the REST API for Pausing/Resuming does not require a body.

## Importing to Synapse.
In Synapse Pipelines, import the zip in this repo. _(more to come here)_

## Optional Pipeline - Pause/Resume All Workspace Pools
