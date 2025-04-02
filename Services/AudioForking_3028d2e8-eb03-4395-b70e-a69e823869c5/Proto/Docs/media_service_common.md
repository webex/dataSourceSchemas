# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [media_service_common.proto](#media_service_common-proto)
    - [AudioDtmfEvents](#com-cisco-wcc-ccai-media-v1-AudioDtmfEvents)
    - [CallEvent](#com-cisco-wcc-ccai-media-v1-CallEvent)
    - [CallStartedDetails](#com-cisco-wcc-ccai-media-v1-CallStartedDetails)
    - [InputTextContent](#com-cisco-wcc-ccai-media-v1-InputTextContent)
    - [StreamControl](#com-cisco-wcc-ccai-media-v1-StreamControl)
    - [SupervisorBargeInDetails](#com-cisco-wcc-ccai-media-v1-SupervisorBargeInDetails)
    - [TransferDetails](#com-cisco-wcc-ccai-media-v1-TransferDetails)
    - [WhisperCoachingDetails](#com-cisco-wcc-ccai-media-v1-WhisperCoachingDetails)
  
    - [AudioEncoding](#com-cisco-wcc-ccai-media-v1-AudioEncoding)
    - [CallEventType](#com-cisco-wcc-ccai-media-v1-CallEventType)
    - [DTMFs](#com-cisco-wcc-ccai-media-v1-DTMFs)
    - [ErrorCode](#com-cisco-wcc-ccai-media-v1-ErrorCode)
    - [ParticipantRole](#com-cisco-wcc-ccai-media-v1-ParticipantRole)
    - [StreamControl.ControlType](#com-cisco-wcc-ccai-media-v1-StreamControl-ControlType)
    - [StreamStatus](#com-cisco-wcc-ccai-media-v1-StreamStatus)
  
- [Scalar Value Types](#scalar-value-types)



<a name="media_service_common-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## media_service_common.proto
common Proto file for the media service flow


<a name="com-cisco-wcc-ccai-media-v1-AudioDtmfEvents"></a>

### AudioDtmfEvents
DTMF input events during the conversation.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| dtmf_digits | [DTMFs](#com-cisco-wcc-ccai-media-v1-DTMFs) | repeated | Sequence of DTMF digits. |
| role | [ParticipantRole](#com-cisco-wcc-ccai-media-v1-ParticipantRole) |  | Role of the participant providing the DTMF input (caller, agent, or supervisor). |
| dtmf_timestamp | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | Timestamp of when the DTMF input was received. |
| user_id | [string](#string) |  | IDs might be numbers or UUIDs. We could change string to specific objects if needed. |






<a name="com-cisco-wcc-ccai-media-v1-CallEvent"></a>

### CallEvent
Call state events (e.g., call start, call end, transfer, etc.).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| event_type | [CallEventType](#com-cisco-wcc-ccai-media-v1-CallEventType) |  |  |
| event_timestamp | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | Timestamp of the event. |
| call_started_details | [CallStartedDetails](#com-cisco-wcc-ccai-media-v1-CallStartedDetails) |  | Parameters for the CALL_STARTED event. |
| custom_event_parameters | [google.protobuf.Struct](#google-protobuf-Struct) |  | Parameters for a custom event. |
| transfer_details | [TransferDetails](#com-cisco-wcc-ccai-media-v1-TransferDetails) |  | For CONSULT_TRANSFER and BLIND_TRANSFER, details of the agent or supervisor involved. |
| whisper_coaching_details | [WhisperCoachingDetails](#com-cisco-wcc-ccai-media-v1-WhisperCoachingDetails) |  | For WHISPER_COACHING, details of the supervisor coaching the agent. |
| supervisor_barge_in_details | [SupervisorBargeInDetails](#com-cisco-wcc-ccai-media-v1-SupervisorBargeInDetails) |  | For SUPERVISOR_BARGE_IN, details of the supervisor joining the conversation. |






<a name="com-cisco-wcc-ccai-media-v1-CallStartedDetails"></a>

### CallStartedDetails
Details for the CALL_STARTED event.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| caller_id | [string](#string) |  | Caller and callee ids might be numbers or UUIDs. We could change string to specific objects if needed. |
| callee_id | [string](#string) |  |  |
| call_direction | [string](#string) |  | Direction of the call (e.g., inbound or outbound) |






<a name="com-cisco-wcc-ccai-media-v1-InputTextContent"></a>

### InputTextContent
Content of the text input


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| text | [string](#string) |  | Plain text input. |
| ssml | [string](#string) |  | Optional. SSML formatted text input. |
| language_code | [string](#string) |  | Language code ofF the user input, e.g., &#39;en-US&#39;. |






<a name="com-cisco-wcc-ccai-media-v1-StreamControl"></a>

### StreamControl
Control message to pause, resume, or stop the stream.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| control_type | [StreamControl.ControlType](#com-cisco-wcc-ccai-media-v1-StreamControl-ControlType) |  |  |






<a name="com-cisco-wcc-ccai-media-v1-SupervisorBargeInDetails"></a>

### SupervisorBargeInDetails
Details for supervisor barge-in events.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| supervisor_id | [string](#string) |  | The supervisor joining the conversation. |
| silent_barge | [bool](#bool) |  | Indicates if the barge-in is silent or the supervisor can speak. |






<a name="com-cisco-wcc-ccai-media-v1-TransferDetails"></a>

### TransferDetails
Details for transfer events.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transferror_id | [string](#string) |  | IDs may be UUIDs or phone numbers. A URN format might be helpful here. |
| transferree_id | [string](#string) |  |  |
| transfer_to_id | [string](#string) |  |  |






<a name="com-cisco-wcc-ccai-media-v1-WhisperCoachingDetails"></a>

### WhisperCoachingDetails
Details for whisper coaching events.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| supervisor_id | [string](#string) |  | The supervisor providing whisper coaching. |
| agent_id | [string](#string) |  | The agent being coached. |





 


<a name="com-cisco-wcc-ccai-media-v1-AudioEncoding"></a>

### AudioEncoding
Encoding format of the audio data.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSPECIFIED | 0 |  |
| LINEAR16 | 1 | 16-bit linear PCM. |
| MULAW | 2 | G.711 mu-law. |
| ALAW | 3 | G.711 A-law. |



<a name="com-cisco-wcc-ccai-media-v1-CallEventType"></a>

### CallEventType


| Name | Number | Description |
| ---- | ------ | ----------- |
| EVENT_UNSPECIFIED | 0 |  |
| CALL_STARTED | 1 | Indicates the call has started. |
| CALL_ENDED | 2 | Indicates the call has ended. |
| TRANSFER_TO_AGENT | 3 | Call is being transferred to a human agent. |
| ON_HOLD | 4 | Call is placed on hold. |
| OFF_HOLD | 5 | Call is resumed. |
| MUTE | 6 | The call is muted. |
| UNMUTE | 7 | The call is unmuted. |
| CONSULT_TRANSFER | 8 | Indicates a consult transfer. |
| BLIND_TRANSFER | 9 | Indicates a blind transfer. |
| WHISPER_COACHING | 10 | Indicates whisper coaching for the agent. |
| SUPERVISOR_BARGE_IN | 11 | Indicates supervisor barge-in to the conversation. |
| CUSTOM_EVENT | 12 | Any custom event related to the call. |



<a name="com-cisco-wcc-ccai-media-v1-DTMFs"></a>

### DTMFs
DTMF digits, including A, B, C, and D.

| Name | Number | Description |
| ---- | ------ | ----------- |
| DTMF_UNSPECIFIED | 0 |  |
| DTMF_ONE | 1 | Number: &#39;1&#39;. |
| DTMF_TWO | 2 | Number: &#39;2&#39;. |
| DTMF_THREE | 3 | Number: &#39;3&#39;. |
| DTMF_FOUR | 4 | Number: &#39;4&#39;. |
| DTMF_FIVE | 5 | Number: &#39;5&#39;. |
| DTMF_SIX | 6 | Number: &#39;6&#39;. |
| DTMF_SEVEN | 7 | Number: &#39;7&#39;. |
| DTMF_EIGHT | 8 | Number: &#39;8&#39;. |
| DTMF_NINE | 9 | Number: &#39;9&#39;. |
| DTMF_ZERO | 10 | Number: &#39;10&#39;. |
| DTMF_A | 11 | Letter: &#39;A&#39;. |
| DTMF_B | 12 | Letter: &#39;B&#39;. |
| DTMF_C | 13 | Letter: &#39;C&#39;. |
| DTMF_D | 14 | Letter: &#39;D&#39;. |
| DTMF_STAR | 15 | Asterisk/star: &#39;*&#39;. |
| DTMF_POUND | 16 | Pound/diamond/hash/square/gate/octothorpe: &#39;#&#39;. |



<a name="com-cisco-wcc-ccai-media-v1-ErrorCode"></a>

### ErrorCode
Enumeration for non-functional error handling.

| Name | Number | Description |
| ---- | ------ | ----------- |
| ERROR_NONE | 0 |  |
| ERROR_INVALID_AUDIO_FORMAT | 1 |  |
| ERROR_INVALID_DTMF | 2 |  |
| ERROR_CALL_EVENT_MISSING | 3 |  |
| ERROR_STREAM_FAILURE | 4 |  |



<a name="com-cisco-wcc-ccai-media-v1-ParticipantRole"></a>

### ParticipantRole
Role of the participant providing transcript or DTMF input.

| Name | Number | Description |
| ---- | ------ | ----------- |
| ROLE_UNSPECIFIED | 0 |  |
| CALLER | 1 |  |
| AGENT | 2 |  |
| SUPERVISOR | 3 | Supervisor role is not supported yet from Webex side and this field is relevant for future development |



<a name="com-cisco-wcc-ccai-media-v1-StreamControl-ControlType"></a>

### StreamControl.ControlType


| Name | Number | Description |
| ---- | ------ | ----------- |
| CONTROL_UNSPECIFIED | 0 |  |
| PAUSE | 1 | Request to pause the stream. |
| RESUME | 2 | Request to resume the stream. |
| STOP | 3 | Request to stop the stream. |



<a name="com-cisco-wcc-ccai-media-v1-StreamStatus"></a>

### StreamStatus
Indicates the current status of the stream from the client side.

| Name | Number | Description |
| ---- | ------ | ----------- |
| STREAM_STATUS_UNSPECIFIED | 0 |  |
| INACTIVE | 1 | The stream has not started. |
| ACTIVE | 2 | The stream is currently active. |
| PAUSED | 3 | The stream is paused. |


 

 

 



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

