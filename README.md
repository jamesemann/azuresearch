# azuresearch

This demo shows how to create an Azure Search Instance and index JSON files stored in an associated Blob Storage account.

1. The ARM template will deploy both Search and Blob Storage using the button below.  Note - keep the search and blob names short as there is a maximum length of 24 characters and the ARM template will add a guid to the end of the value you provide.

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://azuredeploy.net/)

2. Once this has been created, you need to create an index

3. Once the index has been created, add a data source and upload a sample file to it

4. Once the data source has been added, then you need to add an indexer, which maps the data source to the index


