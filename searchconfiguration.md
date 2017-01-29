#Register datasource

POST https://srchkg44a424r354y.search.windows.net/datasources?api-version=2015-02-28-Preview
Content-Type: application/json
api-key: 356FACCD51C32DE3D49336ADE3658F6F

{
    "name" : "blob-datasource",
    "type" : "azureblob",
    "credentials" : { "connectionString" : "DefaultEndpointsProtocol=https;AccountName=blobskg44a424r354y;AccountKey=7pIX9zmYyd7QYzELhaFxxefDpuARL7jsn4HeVX3Sq850l0K7O2IQFiOBvjlUQOJsh8BudeymQvTlfO2xkCqjGw==" },
    "container" : { "name" : "allblobs" }
}   



#Then add indexers

POST https://srchkg44a424r354y.search.windows.net/indexers?api-version=2015-02-28-Preview
Content-Type: application/json
api-key: 356FACCD51C32DE3D49336ADE3658F6F

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
