# Object Encryption
 - Serv3er-side encryption (SSE)
    - Ser-side encrution with S3 manaed keys  (SSE S3)  (Eanled by defalut)
    - Server-side Encrytion with KMS keys Stored in AWS KMS (sse KMS)
    - Sever-side encryption using customer provided keys (SSE-c)
 - Client Side Encrytion
# SSE-S3
 - using keys handled, managed and owned by AWS
 - Object is encrypted server-side
 - Encryption type is AES-256
 - must set header "x-amz-server-side-encrytion":"AES256"
 - default for new bucket and new object
# SSE KMS
 - use keys hanndle and managged by KMS
 - KMS pros: user control + audit key usage using CloudTrail
 - Object is encrypted server side
 - header set to "X-AMZ-server-side-encryption":"AWS:KMS"
 - limitation:
   - depend on the KMS likmits
   - when uplaod it call GenerateDataKey KMS API
   - when Download it call the Decrypt KMS API
   - cont towards the KMS quota per second (based on region)
# SSE -C
   
