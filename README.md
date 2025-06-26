# About
This repository includes schema definitions, used while creating BYoDS service apps. There is a unique schema for each use case.
Schema definition is nothing but a defined structure which includes payload and other information for a specific use case.These schema definitions are defined and published by Webex teams so that partners/customers can build their side of solutions leveraging the defined format.
For example Voice virtual agent schema incldues the structure information of voice virtual agent use case. Which is used by contact center platform and partners/customers to build solution.
Developers need to go to respective service folder, go through the schema definitions to validate if it matches their use case. If not new schema deifnition has to be created and approved by webex teams, matching your use case.
To know more about the BYoDS framework, please refer our developer portal-
https://developer.webex.com/create/docs/bring-your-own-datasource

# Supported use-cases
## Voice Virtual Agent 
Please refer voiceVirtualAgent schema definition to build the solution for BYoVA on top of webex contact center.
## Media forking
Please refer mediaForking schema definition to build the solution for media forking on top of webex contact center.

# Schema structure
## Schema defintion location
Schema defintion of each use case is defined as per below folder structure-
Services->schema name->schema id->schema.json
**Example** - Path of voice virtual agent schema is Services/VoiceVirtualAgent/5397013b-7920-4ffc-807c-e8a3e0a18f43/schema.json

## Fields in schema defintion
**Schema name** - Name of the defined schema.
**Schema id** - Unique id(uuid) assigned to the schema.
**Protocol** - gRPC or REST
**Payload** - version(version of the payload),requestSchema(request payload structure) and responseSchema(response payload structure).
**SupportedAppType** - serviceApp or bot

**Example** -
Voice virtual agent schema definition
```
{
    "schemaId": "5397013b-7920-4ffc-807c-e8a3e0a18f43",
    "serviceName": "Voice Virtual Agent Service",
    "protocol": "gRPC",
    "payload": {
        "version": "1.0",
        "requestSchema": {
            "uri": "https://github.com/webex/dataSourceSchemas/blob/v1.8/Services/VoiceVirtualAgent/5397013b-7920-4ffc-807c-e8a3e0a18f43/Proto/voicevirtualagent.proto"
        },
        "responseSchema": {
            "uri": "https://github.com/webex/dataSourceSchemas/blob/v1.8/Services/VoiceVirtualAgent/5397013b-7920-4ffc-807c-e8a3e0a18f43/Proto/voicevirtualagent.proto"
        }
    },
    "supportedAppType": "serviceApp"
}
```
**Proto definitions**-
Services->VoiceVirtualAgent->5397013b-7920-4ffc-807c-e8a3e0a18f43->Proto
Services->VoiceVirtualAgent->5397013b-7920-4ffc-807c-e8a3e0a18f43->Proto->Docs

## General guidelines for schema
1. requestSchema and responseSchema need to point to defined payload files(path needs to be mentioned in uri).
2. For gRPC request and response payload will be in the form of Proto files and for REST, it will be JSON.
3. Documenation of the request and response proto files should be given in Services->schema name-> Proto->Docs in the form of md files for gRPC.
4. Documenation of the request and response JSON files should be given in Services->schema name-> JSON ->Docs in the form of API spec for REST.
5. Payloads should be backward compatible. This means newer version should be backward compatible.

# Contribution
This repository is a read-only repository and will be used only to read the existing schema defintions and supported files.
Schema defintions can only be published by webex internal teams.

# Git versioning and new release
Whenever new changes are published to this branch, a new relase tag will be generated and the changes will be reflected in latest release tag.
Changes done for a specific release tag will be mentioned in notes.

# Issues
https://developer.webex.com/support
devsupport@webex.com
Maintainers

This project is maintained by Cisco Webex for Developers.

# glossary
**BYoDS** - Bring your own Data Source - https://developer.webex.com/create/docs/bring-your-own-datasource
**BYoVA** - Bring your own virtual agent - https://developer.webex.com/webex-contact-center/docs/bring-your-own-virtual-agent



