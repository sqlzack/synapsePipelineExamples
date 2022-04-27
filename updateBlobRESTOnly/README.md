## Append API Response to file REST Only
This pipeline is inspired from the one in [this video](https://www.youtube.com/watch?v=i4xz2haDlOg). It can be used for appending responses from an API to a file that will utlimately be very small (~2MB). Although Synape is not intended to be used as a message processor this could be used as a way to scrape for an event to kick off a larger pipeline

## Parameters
- storagename - The globally unuqie name of your storage account.
- filepath - The path in storage to your file starting with a leading slash (/raw/updatefile.txt).
- container - The storage container your file is stored in.

## Importing to Synapse.
In Synapse Pipelines, import the zip in this repo. _(more to come here)_