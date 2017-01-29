POST https://<searchname>.search.windows.net/indexes?api-version=2015-02-28-Preview
Content-Type: application/json
api-key: <apikey>

#Create index
{
 "name": "default",  
 "fields": [
  {"name": "id", "type": "Edm.String", "key": true, "searchable": false},
  {"name": "businessname", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true},
 ]
}


#Register datasource

POST https://<searchname>.search.windows.net/datasources?api-version=2015-02-28-Preview
Content-Type: application/json
api-key: <apikey>

{
    "name" : "blob-datasource",
    "type" : "azureblob",
    "credentials" : { "connectionString" : "DefaultEndpointsProtocol=https;AccountName=<blobname>;AccountKey=<blobaccountkey>" },
    "container" : { "name" : "allblobs" }
}   



#Then add indexers

POST https://<searchname>.search.windows.net/indexers?api-version=2015-02-28-Preview
Content-Type: application/json
api-key: <apikey>

{
  "name" : "bob-json-indexer",
  "dataSourceName" : "blob-datasource",
  "targetIndexName" : "default",
  "schedule" : { "interval" : "PT2H" },
  "parameters" : { "configuration" : { "parsingMode" : "jsonArray", "documentRoot" : "/FHRSEstablishment/EstablishmentCollection/EstablishmentDetail" } },
  "fieldMappings" : [
    { "sourceFieldName" : "/FHRSID", "targetFieldName" : "id" },
    { "sourceFieldName" : "/BusinessName", "targetFieldName" : "businessname" }
    ]
}
