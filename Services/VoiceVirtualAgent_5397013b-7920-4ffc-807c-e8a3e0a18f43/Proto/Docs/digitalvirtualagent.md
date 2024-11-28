# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [digitalvirtualagent.proto](#digitalvirtualagent-proto)
    - [DigitalVAOutputEvent](#com-cisco-wcc-ccai-media-v1-DigitalVAOutputEvent)
    - [DigitalVirtualAgentRequest](#com-cisco-wcc-ccai-media-v1-DigitalVirtualAgentRequest)
    - [DigitalVirtualAgentResponse](#com-cisco-wcc-ccai-media-v1-DigitalVirtualAgentResponse)
    - [TextResponse](#com-cisco-wcc-ccai-media-v1-TextResponse)
  
    - [DigitalInputMode](#com-cisco-wcc-ccai-media-v1-DigitalInputMode)
    - [DigitalVAOutputEvent.DigitalVaEventType](#com-cisco-wcc-ccai-media-v1-DigitalVAOutputEvent-DigitalVaEventType)
  
    - [DigitalVirtualAgent](#com-cisco-wcc-ccai-media-v1-DigitalVirtualAgent)
  
- [Scalar Value Types](#scalar-value-types)



<a name="digitalvirtualagent-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## digitalvirtualagent.proto
This proto file has APIs for retrieving Digital virtual agent responses from the the upstream
For the audio virtual agent requests that is sent from media service, relevant streaming
audio virtual response will be sent by the upstream connectors.


<a name="com-cisco-wcc-ccai-media-v1-DigitalVAOutputEvent"></a>

### DigitalVAOutputEvent
Events that represent the state of the session or interaction.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| event_type | [DigitalVAOutputEvent.DigitalVaEventType](#com-cisco-wcc-ccai-media-v1-DigitalVAOutputEvent-DigitalVaEventType) |  | event type |
| parameters | [google.protobuf.Struct](#google-protobuf-Struct) |  | Optional: additional event parameters. |






<a name="com-cisco-wcc-ccai-media-v1-DigitalVirtualAgentRequest"></a>

### DigitalVirtualAgentRequest
Represents the Request format for Digital virtual agent request


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| conversation_id | [string](#string) |  | Conversation id (mapped to call id) |
| customer_org_id | [string](#string) |  | Customer organization ID. |
| virtual_agent_id | [string](#string) |  | ID of the virtual agent that must be invoked. |
| allow_partial_responses | [bool](#bool) |  | Indicates whether partial responses from the virtual agent are allowed. |
| vendor_specific_config | [string](#string) |  | Opaque object (JSON string?) carrying vendor-specific configuration or identifiers. |
| text_input | [TextContent](#com-cisco-wcc-ccai-media-v1-TextContent) |  | The text input from the user (plain text or SSML). |
| dtmf_input | [DTMFInputs](#com-cisco-wcc-ccai-media-v1-DTMFInputs) |  | Optional. DTMF events during the interaction. |
| event_input | [InputEvent](#com-cisco-wcc-ccai-media-v1-InputEvent) |  | Optional. Input events, such as session start, session end, custom events, etc. |






<a name="com-cisco-wcc-ccai-media-v1-DigitalVirtualAgentResponse"></a>

### DigitalVirtualAgentResponse
Represents the output of the digital virtual agent, which includes
response text and events.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| text_responses | [TextResponse](#com-cisco-wcc-ccai-media-v1-TextResponse) | repeated | List of text responses to be sent back to the user. |
| output_events | [DigitalVAOutputEvent](#com-cisco-wcc-ccai-media-v1-DigitalVAOutputEvent) | repeated | Output events from the virtual agent, such as session end, transfer to human agent, or custom events. |
| input_sensitive | [bool](#bool) |  | Indicates whether the next input from the client is to be considered sensitive (e.g., for PCI compliance). |
| is_partial | [bool](#bool) |  | Indicates whether the response is partial or final. |
| input_mode | [DigitalInputMode](#com-cisco-wcc-ccai-media-v1-DigitalInputMode) |  | Input mode for the next expected input (text, DTMF, or both). |
| input_handling_config | [InputHandlingConfig](#com-cisco-wcc-ccai-media-v1-InputHandlingConfig) |  | Speech timers and DTMF configuration for handling input. |






<a name="com-cisco-wcc-ccai-media-v1-TextResponse"></a>

### TextResponse
Text response format


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| text | [string](#string) |  | Plain text response. |
| ssml | [string](#string) |  | SSML formatted response. |
| final_chunk | [bool](#bool) |  | Indicates whether the response is the final chunk of a multi-part message. |
| caller_can_interrupt_va | [bool](#bool) |  | Whether the caller can barge in before the prompt is completely played out |





 


<a name="com-cisco-wcc-ccai-media-v1-DigitalInputMode"></a>

### DigitalInputMode
Type of input expected from the user.

| Name | Number | Description |
| ---- | ------ | ----------- |
| INPUT_MODE_UNSPECIFIED | 0 | unspecified input |
| INPUT_TEXT | 1 | text input |
| INPUT_DTMF | 2 | voice dtmf input |
| INPUT_TEXT_DTMF | 3 | text dtmf input |



<a name="com-cisco-wcc-ccai-media-v1-DigitalVAOutputEvent-DigitalVaEventType"></a>

### DigitalVAOutputEvent.DigitalVaEventType
Type of events

| Name | Number | Description |
| ---- | ------ | ----------- |
| EVENT_UNSPECIFIED | 0 | unspecified event |
| DIGITAL_VA_SESSION_END | 1 | The session with the virtual agent has ended. |
| TRANSFER_TO_AGENT | 2 | Transfer the interaction to a human agent. |
| CUSTOM | 3 | A custom event based on interaction logic. |


 

 


<a name="com-cisco-wcc-ccai-media-v1-DigitalVirtualAgent"></a>

### DigitalVirtualAgent
Service definition for the Digital Virtual Agent gRPC API.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| ProcessCallerInput | [DigitalVirtualAgentRequest](#com-cisco-wcc-ccai-media-v1-DigitalVirtualAgentRequest) stream | [DigitalVirtualAgentResponse](#com-cisco-wcc-ccai-media-v1-DigitalVirtualAgentResponse) stream | Bidirectional streaming RPC to send and receive text, DTMF or input events. |
| ListVirtualAgents | [ListVARequest](#com-cisco-wcc-ccai-media-v1-ListVARequest) | [ListVAResponse](#com-cisco-wcc-ccai-media-v1-ListVAResponse) | The Service that takes virtual agent list request and org id and returns a list of bots |

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

