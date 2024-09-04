#Description

This repository includes schema definitions for BYoDS solution of webex. These schema defintions will be used to register the data source with webex. Please go to respective service folder, go through the schema defintions and respective payload defintions to validate if it matches your use case. If not new chema deifntion has to be created and approved by webex teams, matching your use case.

##schema structure


| Property name  | Description |optional/mandatory |
| ------------- | ------------- | ------------ |
| schemaId  | Unique id(UUID) or enum  | mandatory |
| serviceName  | Name of the service( summarisation service, search service etc)  | mandatory |
| protocol  | REST or gRPC  | mandatory |
| schemaHash  | Hash(sha256) of the schema payload  | mandatory |
| version  | version of req/response schema  | mandatory |
| payloadUrl  | Full payload file Url(including request and response format in a single json or proto file)  | Optional |
| requestSchema  | Each service should define and should be published on dev-portal  | Optional |
| requestSchemaUrl  | file url which contains request payload definition  | Optional |
| requestSchemaHash  | Hash(sha256) of the request payload In case of gRPC it could be hash of proto files/folder | mandatory |
| responseSchema  | Each service should define and should be published on dev-portal  | Optional |
| responseSchemaUrl  | file url which contains response payload definition  | Optional |
| responseSchemaHash  | Hash(sha256) of the response payload In case of gRPC it could be hash of proto files/folder  | Mandatory |
| supportedAppType  | ServiceApp/Bot(bot only used for typeAhead)  | mandatory |
| quality parameters  | as of now latency is included in quality parameters | Optional |


#Contribute

This repository is a read-only repository and will be used only to read the existing schema defintions and supported files.
Schema defintions can only be published by webex internal teams.

#Issues

https://developer.webex.com/support
devsupport@webex.com

#Maintainers

This project is maintained by Cisco Webex for Developers.


