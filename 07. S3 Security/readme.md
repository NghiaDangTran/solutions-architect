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
 - customer keys
 - S3 does not store the key
 - HTTPS muse be used
 - key must provided in HTTP headers for every HTTP request made
# Client side encryption
 - use client libraty lie S3 client encryption library
 - clients must encrypt data themselves before send to S3
 - clients decrypt when retreive data
 - customer manges kes and encrption cucle
# Encryiopn in tranist (SSL/TLS)
 - encrytion in fly is also called SSL/TLS
 - expose 2 endpoitns ettps  and https
 - https is recommeded
 - https is mandatory for SSE-c
# set HHTPS by set sercureTranport: True
# Decault Encrypption vs bucket Policeis 
 - SSE-S3 encryption is automatically applied to new objets stored in S3 bucket
 - optional set policy  to refuse any PUt without encrytion headers
 - NOte: `Buket Polices are evaluated before default encrytion`
# S3 CORS:
 - cross origin resource Sharing
 - lorigin =Scheme (protocal) + host  (domain) +port
 - web broswer based mechanism to allow request to other origins while visiting the main origin
 - same orggin  hhtps//example/app1 and https/ecample/app2
 - other origin https:// wweample.com  and https://api.emaple.com
 - set access control allow origin and methods
 - enable bucket specific origin or *
# S3 MFA delete
 - MFA force users to generate a code on a device before doingg important operations on S3
 - requpre to permanelty delte, supend versioning
 - dont require to eable versioning, list deleted version
 - to use MFA delete, versioin must be eabled on the bucket
 - only the bucket owner  (root account) can be enable/disable MFA delete
 # S3 Acess logs
  - for audit u may want to loag all access to s3 bucket
  - the target logging bucket must be in the same AWS region
  - dont set this bucket to monitored ucker else it will create infinity loop
# S3 per-signer URLs
 - generate presigned URLS using the S3 console, AWS CLI or SDK
 - URL expriation: S# console, AWS CLi
 - make that url for GET /PUT
# Glacier Vault lock
 - Adopt a Write Once Read Many
 - lock the policy for fure edits  (can no longer be chaned or deleted)
 - delful for compliance and data retention
# Object Lock (versioning must be eabled)
 - • Retention mode - Compliance:
   - • Object versions can't be overwritten or deleted by any user, including the root user
   - • Objects retention modes can't be changed, and retention periods can't be shortened •
 - Retention mode - Governance: •
   - Most users can't overwrite or delete an object version or alter its lock settings •
   - Some users have special permissions to change the retention or delete the object •
 - Retention Period: protect the object for a fixed period, it can be extended •
 - Legal Hold: •
   - protect the object indefinitely, independent from retention period •
    - can be freely placed and removed using the s3:PutObjectLegalHold IAM permission
  # S3 Access Points
   - set a folder or something to R or W
   - it own DNS name (internet origin or VPC orgin)
   - mange at scale
 # S3 Obnject Lambda
 
 is a feature of Amazon S3 that allows you to add custom code to process data as it is retrieved from S3. Before S3 Object Lambda, if you wanted to transform or process your data stored in S3 during retrieval, you'd typically need to build a separate application layer to fetch, process, and return the data. With S3 Object Lambda, you can achieve this directly within the S3 retrieval process.
