# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [voicevirtualagent.proto](#voicevirtualagent-proto)
    - [Prompt](#com-cisco-wcc-ccai-media-v1-Prompt)
    - [VoiceInput](#com-cisco-wcc-ccai-media-v1-VoiceInput)
    - [VoiceVARequest](#com-cisco-wcc-ccai-media-v1-VoiceVARequest)
    - [VoiceVAResponse](#com-cisco-wcc-ccai-media-v1-VoiceVAResponse)
  
    - [VoiceInput.VoiceEncoding](#com-cisco-wcc-ccai-media-v1-VoiceInput-VoiceEncoding)
    - [VoiceVAInputMode](#com-cisco-wcc-ccai-media-v1-VoiceVAInputMode)
  
    - [VoiceVirtualAgent](#com-cisco-wcc-ccai-media-v1-VoiceVirtualAgent)
  
- [Scalar Value Types](#scalar-value-types)



<a name="voicevirtualagent-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## voicevirtualagent.proto
This proto file has APIs for retrieving Audio virtual agent responses from the the upstream
For the Voice virtual agent requests that is sent from media service, relevant streaming
Voice virtual response will be sent by the upstream connectors.


<a name="com-cisco-wcc-ccai-media-v1-Prompt"></a>

### Prompt
Describes the prompt (Voice or text) to be played to the caller.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| text | [string](#string) |  | Text of the prompt (if available). |
| audio_uri | [string](#string) |  | URI of the audio to be played. |
| audio_content | [bytes](#bytes) |  | Raw audio content. |
| is_final_chunk | [bool](#bool) |  | Whether this is the final chunk of audio. |
| is_barge_in_enabled | [bool](#bool) |  | Whether the caller can barge in before the prompt is completely played out |






<a name="com-cisco-wcc-ccai-media-v1-VoiceInput"></a>

### VoiceInput
Represents the voice input object


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| caller_audio | [bytes](#bytes) |  | The raw audio bytes for the caller&#39;s audio stream. |
| encoding | [VoiceInput.VoiceEncoding](#com-cisco-wcc-ccai-media-v1-VoiceInput-VoiceEncoding) |  |  |
| sample_rate_hertz | [int32](#int32) |  | Sampling rate of the input audio in Hertz. |
| audio_timestamp | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | Start timestamp of when the audio data was captured. |
| language_code | [string](#string) |  | Language code of the caller, e.g., &#39;en-US&#39;. |
| is_single_utterance | [bool](#bool) |  | Indicates if the audio content represents a single utterance. |






<a name="com-cisco-wcc-ccai-media-v1-VoiceVARequest"></a>

### VoiceVARequest
Represents the Request format for voice virtual agent


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| conversation_id | [string](#string) |  | Conversation id - mapped to call id. |
| customer_org_id | [string](#string) |  | Customer organization ID. |
| virtual_agent_id | [string](#string) |  | ID of the virtual agent that must be invoked. |
| allow_partial_responses | [bool](#bool) |  | Indicates whether partial responses from the virtual agent are allowed. |
| vendor_specific_config | [string](#string) |  | Opaque object (JSON string?) carrying vendor-specific configuration or identifiers. |
| audio_input | [VoiceInput](#com-cisco-wcc-ccai-media-v1-VoiceInput) |  | The voice input from the caller. |
| dtmf_input | [DTMFInputs](#com-cisco-wcc-ccai-media-v1-DTMFInputs) |  | Optional. DTMF events during the call. |
| event_input | [EventInput](#com-cisco-wcc-ccai-media-v1-EventInput) |  | Optional. Input events, such as call start, call end, no input, etc. |






<a name="com-cisco-wcc-ccai-media-v1-VoiceVAResponse"></a>

### VoiceVAResponse
Represents the output of the virtual agent, which includes response audio,
events, and configurations.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| prompts | [Prompt](#com-cisco-wcc-ccai-media-v1-Prompt) | repeated | List of prompt Voice responses to be played by the caller. |
| output_events | [OutputEvent](#com-cisco-wcc-ccai-media-v1-OutputEvent) | repeated | Output events from the virtual agent, such as session end or transfer to human agent. As of now only one event will be supported and first event will be considered. |
| input_sensitive | [bool](#bool) |  | Indicates whether the next input from the client is to be considered sensitive (e.g., for PCI compliance). |
| is_partial | [bool](#bool) |  | Indicates whether the response is partial or final. |
| input_mode | [VoiceVAInputMode](#com-cisco-wcc-ccai-media-v1-VoiceVAInputMode) |  | Input mode for next input |
| input_handling_config | [InputHandlingConfig](#com-cisco-wcc-ccai-media-v1-InputHandlingConfig) |  | Speech timers and DTMF configuration for handling input. |
| session_transcript | [TextContent](#com-cisco-wcc-ccai-media-v1-TextContent) |  | Optional. Final transcript of entire session, typically included in last response. Transcripts included in intermediate responses are ignored. |
| session_summary | [TextContent](#com-cisco-wcc-ccai-media-v1-TextContent) |  | Optional. Summary of the session, included in the last response. Summary included in intermediate responses are ignored. SSML does not make sense for summary. Using TextContent so that language code can be used. |





 


<a name="com-cisco-wcc-ccai-media-v1-VoiceInput-VoiceEncoding"></a>

### VoiceInput.VoiceEncoding
Encoding format of the audio data.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSPECIFIED_FORMAT | 0 |  |
| LINEAR16_FORMAT | 1 | 16-bit linear PCM. |
| MULAW_FORMAT | 2 | G.711 mu-law. |
| ALAW_FORMAT | 3 | G.711 A-law. |



<a name="com-cisco-wcc-ccai-media-v1-VoiceVAInputMode"></a>

### VoiceVAInputMode
Type of input expected from user

| Name | Number | Description |
| ---- | ------ | ----------- |
| INPUT_VOICE_MODE_UNSPECIFIED | 0 | unspecified input |
| INPUT_VOICE | 1 | voice input |
| INPUT_EVENT_DTMF | 2 | event dtmf input |
| INPUT_VOICE_DTMF | 3 | voice dtmf input |


 

 


<a name="com-cisco-wcc-ccai-media-v1-VoiceVirtualAgent"></a>

### VoiceVirtualAgent
Service definition for the Audio Virtual Agent gRPC API.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| ProcessCallerInput | [VoiceVARequest](#com-cisco-wcc-ccai-media-v1-VoiceVARequest) stream | [VoiceVAResponse](#com-cisco-wcc-ccai-media-v1-VoiceVAResponse) stream | Bidirectional streaming RPC to send and receive caller audio, DTMF, or input events. |
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

