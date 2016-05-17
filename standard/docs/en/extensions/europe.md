# Europe - Tenders Electronic Daily

[Tenders Electronic Daily](http://ted.europa.eu/) is the public procurement journal of the European Union. It contains information on business opportunities from the European Union, the European Economic Area and beyond. European public bodies are obliged to publish tender and award notices over a certain threshold with TED, ideally through sending XML notices via the eSender framework. Data from TED is exported in a similar XML format.

This page documents a collection of extensions that can be used to:

* Represented data from TED in OCDS JSON;
* Capture all the details required by key EU Procurement Forms using OCDS;

## Use cases
All extensions to OCDS should be grounded in clear use cases. There are two main use cases for the ability to express TED Notices via OCDS releases and records.

### Use case 1: OCDS -> TED

[The OpenProcurement project](http://openprocurement.org/en/) provides an open platform for managing procurement. It makes use of OCDS for its internal data model, and for API inputs and outputs. 

It is currently in us in Ukraine, and is available as open source software for use in other countries and contexts.

In future, some of the tenders, awards and contracts in the OpenProcurement platform may need to be also posted to the European Journal via TED XML.

This requires:

(a) An agreed mapping between OCDS and required TED elements;
(b) An agreed approach to capture additional required information for TED which is not covered by OCDS;

### Use case 2: TED -> OCDS

A growing range of tools are being developed to analyse OCDS data. These can operate on data from different countries and continents.

An intermediary is interested in converting TED XML exports into OCDS format, in order to enable the use of existing OCDS tooling. 

In line with the OCDS principle of not throwing data away, this means there should be a way to capture additional TED XML fields within OCDS, and, where these have global relevance, to render them in a common way. 

## Mapping and extensions

### Addresses 

OCDS contains fields for addresses of: 

* ```buyer``` 
* ```procuringEntity```
* ```suppliers```

TED has space for:

* Multiple CONTRACTING_BODY values in ADDRESS\_CONTRACTING\_BODY\_ADDITIONAL fields
* ADDRESS\_FURTHER\_INFO where 'Additional information can be obtained from'
* ADDRESS_PARTICIPATION where 'Tenders or requests to participate must be submitted'. This only needs to be provided

For ADDRESS\_FURTHER\_INFO and ADDRESS_PARTICIPATION the XML can contain a boolean field called 'ADDRESS\_PARTICIPATION\_IDEM' (or similar) which indicates that the previously given address should be used for this. 

The [address.json-patch](../../schema/TED/address.json-patch) proposes adding additional address entries to the top level of a release (for additional contracting bodies) and to tender (for further info and participation).


