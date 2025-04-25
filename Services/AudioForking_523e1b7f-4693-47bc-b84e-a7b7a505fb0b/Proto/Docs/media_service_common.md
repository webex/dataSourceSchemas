# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [media_service_common.proto](#media_service_common-proto)
    - [InputTextContent](#com-cisco-wcc-ccai-media-v1-InputTextContent)
  
    - [AudioEncoding](#com-cisco-wcc-ccai-media-v1-AudioEncoding)
    - [ErrorCode](#com-cisco-wcc-ccai-media-v1-ErrorCode)
    - [ParticipantRole](#com-cisco-wcc-ccai-media-v1-ParticipantRole)
  
- [Scalar Value Types](#scalar-value-types)



<a name="media_service_common-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## media_service_common.proto
common Proto file for the media service flow


<a name="com-cisco-wcc-ccai-media-v1-InputTextContent"></a>

### InputTextContent
Content of the text input


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| text | [string](#string) |  | Plain text input. |
| ssml | [string](#string) |  | Optional. SSML formatted text input. |
| language_code | [string](#string) |  | Language code ofF the user input, e.g., &#39;en-US&#39;. |





 


<a name="com-cisco-wcc-ccai-media-v1-AudioEncoding"></a>

### AudioEncoding
Encoding format of the audio data.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSPECIFIED | 0 |  |
| LINEAR16 | 1 | 16-bit linear PCM. |
| MULAW | 2 | G.711 mu-law. |
| ALAW | 3 | G.711 A-law. |



<a name="com-cisco-wcc-ccai-media-v1-ErrorCode"></a>

### ErrorCode
Enumeration for non-functional error handling.

| Name | Number | Description |
| ---- | ------ | ----------- |
| ERROR_NONE | 0 |  |
| ERROR_INVALID_AUDIO_FORMAT | 1 |  |
| ERROR_STREAM_FAILURE | 2 |  |



<a name="com-cisco-wcc-ccai-media-v1-ParticipantRole"></a>

### ParticipantRole
Role of the participant providing transcript.

| Name | Number | Description |
| ---- | ------ | ----------- |
| ROLE_UNSPECIFIED | 0 |  |
| CALLER | 1 |  |
| AGENT | 2 |  |


 

 

 



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

