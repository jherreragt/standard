# Lots

In some systems, a tender process may be divided into lots, where bidders can bid on one or more lots. 

## Use cases

### Use case 1: Open Procurement

The [Open Procurement API](http://api-docs.openprocurement.org/) supported the [division of contracting processes into lots](http://api-docs.openprocurement.org/en/latest/lots.html), with each lot having it's own status and criteria for a reverse auction process. 

### Use case 2: European Procurement (TED)

Notices in the EU Journal of Public Procurement may divide the tender in a single contracting process into a number of lots. Each lot may have it's own estimated value, award criteria, and duration. 

## Extension

The proposed lots extension ([schema patch](../../schema/lots/lots.json-patch)) adds a new ```lots``` block into the ```tender``` section with a list of available lots and their features.

Each ```item```, ```document``` or ```milestone``` may then have a ```relatedLot``` property (an array) to indicate which lot, or lots, it belongs to. 

## Example

The example below shows an extract from a tender notice with three lots, each lot with a related item. 

```json
{
 "tender": {
  "id": "2016/S 031-050378",
  "lots": [
   {
    "description": "Provision of catering services for this girls school with a mixed 6th form  1,242 students.", 
    "id": "1", 
    "title": "Catering contract for Waldegrave School",
    "status":"active"
   }, 
   {
    "description": "Provision of catering services for this mixed school - 1,216 students.", 
    "id": "2", 
    "title": "Catering contract for Orleans Park School",
    "status":"active"
   }, 
   {
    "description": "Provision of catering services for this mixed primary school 505 pupils.", 
    "id": "3", 
    "title": "Catering contract for Nelson Primary School",
    "status":"active"
   }
  ], 
  "items": [
   {
    "id": "1",
    "relatedLot": "1", 
    "classifications": {
     "scheme": "CPV", 
     "id": "55523100", 
     "uri": "http://cpv.data.ac.uk/code-55523100"
    }, 
    "description": "Provision of catering services for this girls school with a mixed 6th form \u2014 1 242 students.", 
    "title": "Catering contract for Waldegrave School", 
    "additionalClassificpations": [
     {
      "scheme": "CPV", 
      "id": "55524000", 
      "uri": "http://cpv.data.ac.uk/code-55524000"
     }
    ]
   }, 
   {
    "id":"2",
    "relatedLot": "2", 
    "classifications": {
     "scheme": "CPV", 
     "id": "55523100", 
     "uri": "http://cpv.data.ac.uk/code-55523100"
    }, 
    "description": "Provision of catering services for this mixed school \u2014 1 216 students.", 
    "title": "Catering contract for Orleans Park School", 
    "additionalClassificpations": [
     {
      "scheme": "CPV", 
      "id": "55524000", 
      "uri": "http://cpv.data.ac.uk/code-55524000"
     }
    ]
   }, 
   {
    "id":"3",
    "relatedLot": "3", 
    "classifications": {
     "scheme": "CPV", 
     "id": "55523100", 
     "uri": "http://cpv.data.ac.uk/code-55523100"
    }, 
    "description": "Provision of catering services for this mixed primary school \u2014 505 pupils.", 
    "title": "Catering contract for Nelson Primary School", 
    "additionalClassificpations": [
     {
      "scheme": "CPV", 
      "id": "55524000", 
      "uri": "http://cpv.data.ac.uk/code-55524000"
     }
    ]
   }
  ]
 }
}
```