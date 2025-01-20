# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [byova_common.proto](#byova_common-proto)
    - [DTMFInputConfig](#com-cisco-wcc-ccai-media-v1-DTMFInputConfig)
    - [DTMFInputs](#com-cisco-wcc-ccai-media-v1-DTMFInputs)
    - [EventInput](#com-cisco-wcc-ccai-media-v1-EventInput)
    - [InputHandlingConfig](#com-cisco-wcc-ccai-media-v1-InputHandlingConfig)
    - [InputSpeechTimers](#com-cisco-wcc-ccai-media-v1-InputSpeechTimers)
    - [ListVARequest](#com-cisco-wcc-ccai-media-v1-ListVARequest)
    - [ListVAResponse](#com-cisco-wcc-ccai-media-v1-ListVAResponse)
    - [OutputEvent](#com-cisco-wcc-ccai-media-v1-OutputEvent)
    - [TextContent](#com-cisco-wcc-ccai-media-v1-TextContent)
    - [VirtualAgentInfo](#com-cisco-wcc-ccai-media-v1-VirtualAgentInfo)
    - [VirtualAgentInfo.AttributesEntry](#com-cisco-wcc-ccai-media-v1-VirtualAgentInfo-AttributesEntry)
  
    - [DTMFDigits](#com-cisco-wcc-ccai-media-v1-DTMFDigits)
    - [EventInput.EventType](#com-cisco-wcc-ccai-media-v1-EventInput-EventType)
    - [OutputEvent.EventType](#com-cisco-wcc-ccai-media-v1-OutputEvent-EventType)
  
- [Scalar Value Types](#scalar-value-types)



<a name="byova_common-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## byova_common.proto
common Proto file for the media service flow


<a name="com-cisco-wcc-ccai-media-v1-DTMFInputConfig"></a>

### DTMFInputConfig
Configuration for DTMF inputs.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| inter_digit_timeout_msec | [int32](#int32) |  | Timeout between two digits in milliseconds. |
| termchar | [DTMFDigits](#com-cisco-wcc-ccai-media-v1-DTMFDigits) |  | Termination character for DTMF inputs (e.g., &#39;#&#39;). |
| dtmf_input_length | [int32](#int32) |  | Maximum length of DTMF input. |






<a name="com-cisco-wcc-ccai-media-v1-DTMFInputs"></a>

### DTMFInputs
DTMF input digits


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| dtmf_events | [DTMFDigits](#com-cisco-wcc-ccai-media-v1-DTMFDigits) | repeated | Sequence of Telephony DTMF digits. |






<a name="com-cisco-wcc-ccai-media-v1-EventInput"></a>

### EventInput
Represents the Type of Events


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| event_type | [EventInput.EventType](#com-cisco-wcc-ccai-media-v1-EventInput-EventType) |  | input event type |






<a name="com-cisco-wcc-ccai-media-v1-InputHandlingConfig"></a>

### InputHandlingConfig
Configuration for capturing DTMF tones and speech timers.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| dtmf_config | [DTMFInputConfig](#com-cisco-wcc-ccai-media-v1-DTMFInputConfig) |  | DTMF input configurations. |
| speech_timers | [InputSpeechTimers](#com-cisco-wcc-ccai-media-v1-InputSpeechTimers) |  | Represents the timer settings for speech recognition. |






<a name="com-cisco-wcc-ccai-media-v1-InputSpeechTimers"></a>

### InputSpeechTimers
Timers for controlling input collection timing.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| max_speech_timeout_msec | [int32](#int32) |  | Maximum duration of an utterance in milliseconds. |
| complete_timeout_msec | [int32](#int32) |  | Duration of silence after an utterance before concluding it&#39;s complete. |
| incomplete_timeout_msec | [int32](#int32) |  | Duration of silence after an utterance before concluding it&#39;s incomplete. |






<a name="com-cisco-wcc-ccai-media-v1-ListVARequest"></a>

### ListVARequest
Represents the Request format for List virtual agent


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| customer_org_id | [string](#string) |  | Customer organization ID. |
| is_default_answers_enabled | [bool](#bool) |  | default answers enabled / disabled - boolean value |
| is_default_virtual_agent_enabled | [bool](#bool) |  | default virtual agent enabled / disabled - boolean value |






<a name="com-cisco-wcc-ccai-media-v1-ListVAResponse"></a>

### ListVAResponse
Represents the Response format for List virtual agent


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| virtual_agents | [VirtualAgentInfo](#com-cisco-wcc-ccai-media-v1-VirtualAgentInfo) | repeated | Indicates the list of bots for the selected provider |






<a name="com-cisco-wcc-ccai-media-v1-OutputEvent"></a>

### OutputEvent
Events that represent the state of the session or call.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| event_type | [OutputEvent.EventType](#com-cisco-wcc-ccai-media-v1-OutputEvent-EventType) |  | input event type |
| parameters | [google.protobuf.Struct](#google-protobuf-Struct) |  | Optional: additional event parameters.custom event related info can also be passed here |






<a name="com-cisco-wcc-ccai-media-v1-TextContent"></a>

### TextContent
Content of the text input


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| text | [string](#string) |  | Plain text input. |
| ssml | [string](#string) |  | Optional. SSML formatted text input. |
| language_code | [string](#string) |  | Language code ofF the user input, e.g., &#39;en-US&#39;. |






<a name="com-cisco-wcc-ccai-media-v1-VirtualAgentInfo"></a>

### VirtualAgentInfo
Represents the virtual agent information


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| virtual_agent_id | [string](#string) |  | Indicates the bots unique identifier |
| virtual_agent_name | [string](#string) |  | Indicates the bot name |
| is_default | [bool](#bool) |  | Indicates whether the respective bot is a default bot for the selected provider |
| attributes | [VirtualAgentInfo.AttributesEntry](#com-cisco-wcc-ccai-media-v1-VirtualAgentInfo-AttributesEntry) | repeated | Any additional attributes that are required |






<a name="com-cisco-wcc-ccai-media-v1-VirtualAgentInfo-AttributesEntry"></a>

### VirtualAgentInfo.AttributesEntry



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| key | [string](#string) |  |  |
| value | [string](#string) |  |  |





 


<a name="com-cisco-wcc-ccai-media-v1-DTMFDigits"></a>

### DTMFDigits
DTMF digits, including A, B, C, and D.

| Name | Number | Description |
| ---- | ------ | ----------- |
| DTMF_EVENT_UNSPECIFIED | 0 |  |
| DTMF_DIGIT_ONE | 1 | Number: &#39;1&#39;. |
| DTMF_DIGIT_TWO | 2 | Number: &#39;2&#39;. |
| DTMF_DIGIT_THREE | 3 | Number: &#39;3&#39;. |
| DTMF_DIGIT_FOUR | 4 | Number: &#39;4&#39;. |
| DTMF_DIGIT_FIVE | 5 | Number: &#39;5&#39;. |
| DTMF_DIGIT_SIX | 6 | Number: &#39;6&#39;. |
| DTMF_DIGIT_SEVEN | 7 | Number: &#39;7&#39;. |
| DTMF_DIGIT_EIGHT | 8 | Number: &#39;8&#39;. |
| DTMF_DIGIT_NINE | 9 | Number: &#39;9&#39;. |
| DTMF_DIGIT_ZERO | 10 | Number: &#39;10&#39;. |
| DTMF_DIGIT_A | 11 | Letter: &#39;A&#39;. |
| DTMF_DIGIT_B | 12 | Letter: &#39;B&#39;. |
| DTMF_DIGIT_C | 13 | Letter: &#39;C&#39;. |
| DTMF_DIGIT_D | 14 | Letter: &#39;D&#39;. |
| DTMF_DIGIT_STAR | 15 | Asterisk/star: &#39;*&#39;. |
| DTMF_DIGIT_POUND | 16 | Pound/diamond/hash/square/gate/octothorpe: &#39;#&#39;. |



<a name="com-cisco-wcc-ccai-media-v1-EventInput-EventType"></a>

### EventInput.EventType
Possible event types

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSPECIFIED_INPUT | 0 | unspecified event |
| SESSION_START | 1 | Event indicating the start of the interaction. for voice agent its call_start |
| SESSION_END | 2 | Event indicating the end of the interaction.for voice agent its call_end |
| NO_INPUT | 3 | Event indicating no input was received from the user. |
| START_OF_DTMF | 4 | Event indicating start of DTMF input. |



<a name="com-cisco-wcc-ccai-media-v1-OutputEvent-EventType"></a>

### OutputEvent.EventType
Possible types of events

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSPECIFIED_EVENT | 0 | unspecified event |
| SESSION_END | 1 | End of session with the virtual agent. |
| TRANSFER_TO_AGENT | 2 | Transfer the call to a human agent. |
| CUSTOM_EVENT | 3 | Custom event based on interaction. |
| START_OF_INPUT | 4 | Triggers when user utter the first utterance in Voice Input mode or First DTMF is pressed in DTMF Input mode. This event to be used to BargeIn the prompt based on prompt barge-in flag. The event will be sent only if the current prompt being played is bargein enabled or prompt playing is complete. |
| END_OF_INPUT | 5 | Sent when user utterance Voice / DTMF is complete. |
| NO_MATCH | 6 | Sent when utterance did not match any of the accepted input |
| NO_INPUT | 7 | Sent when no audio received with in the expected timeframe |


 

 

 



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

