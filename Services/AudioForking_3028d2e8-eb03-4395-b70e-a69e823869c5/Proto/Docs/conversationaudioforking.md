# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [conversationaudioforking.proto](#conversationaudioforking-proto)
    - [AudioStream](#com-cisco-wcc-ccai-media-v1-AudioStream)
    - [ConversationAudioForkingRequest](#com-cisco-wcc-ccai-media-v1-ConversationAudioForkingRequest)
    - [ConversationAudioForkingResponse](#com-cisco-wcc-ccai-media-v1-ConversationAudioForkingResponse)
  
    - [ConversationAudio](#com-cisco-wcc-ccai-media-v1-ConversationAudio)
  
- [Scalar Value Types](#scalar-value-types)



<a name="conversationaudioforking-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## conversationaudioforking.proto



<a name="com-cisco-wcc-ccai-media-v1-AudioStream"></a>

### AudioStream



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| audio_data | [bytes](#bytes) |  | The raw audio bytes for the stream (either agent or caller). |
| encoding | [AudioEncoding](#com-cisco-wcc-ccai-media-v1-AudioEncoding) |  |  |
| sample_rate_hertz | [int32](#int32) |  | Sampling rate of the input audio in Hz. |
| audio_timestamp | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | Start timestamp of when the audio data was captured. |
| role | [ParticipantRole](#com-cisco-wcc-ccai-media-v1-ParticipantRole) |  | Role of the participant providing the audio (caller, agent, or supervisor). |
| user_id | [string](#string) |  | IDs might be numbers or UUIDs. We could change string to specific objects if needed. |






<a name="com-cisco-wcc-ccai-media-v1-ConversationAudioForkingRequest"></a>

### ConversationAudioForkingRequest
Request message for streaming conversation audio, DTMF, and events.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| conversation_id | [string](#string) |  | Conversation ID - mapped to call ID. |
| customer_org_id | [string](#string) |  | Customer org id. |
| stream_status | [StreamStatus](#com-cisco-wcc-ccai-media-v1-StreamStatus) |  | Indicates the current stream status (e.g., PAUSED or ACTIVE). |
| audio | [AudioStream](#com-cisco-wcc-ccai-media-v1-AudioStream) |  | Audio stream. |
| dtmf_input | [AudioDtmfEvents](#com-cisco-wcc-ccai-media-v1-AudioDtmfEvents) |  | DTMF tones input during the call. |
| call_event | [CallEvent](#com-cisco-wcc-ccai-media-v1-CallEvent) |  | Call state events (e.g., call start, call end). |






<a name="com-cisco-wcc-ccai-media-v1-ConversationAudioForkingResponse"></a>

### ConversationAudioForkingResponse
Response message for server to send control commands or status to the client.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| status_message | [string](#string) |  | Optional acknowledgment or status message. |
| control | [StreamControl](#com-cisco-wcc-ccai-media-v1-StreamControl) |  | Stream control message for pause, resume, or stop actions. |
| error_code | [ErrorCode](#com-cisco-wcc-ccai-media-v1-ErrorCode) |  | Any error codes related to processing the stream (optional). |





 

 

 


<a name="com-cisco-wcc-ccai-media-v1-ConversationAudio"></a>

### ConversationAudio
Service definition for streaming agent and caller audio, DTMF, and call events.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| StreamConversationAudio | [ConversationAudioForkingRequest](#com-cisco-wcc-ccai-media-v1-ConversationAudioForkingRequest) stream | [ConversationAudioForkingResponse](#com-cisco-wcc-ccai-media-v1-ConversationAudioForkingResponse) stream | Bidirectional streaming RPC where the client streams data, and the server sends control commands. |

 



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

