
# S3


##### Server Side Encryption
 - Amazon S3 supports the following types o**f server-side encryption**
	- Server-side encryption with Amazon S3 managed keys (SSE-S3)
	- Server-side encryption with AWS Key Management Service (AWS KMS) keys (SSE-KMS)
	- Dual-layer server-side encryption with AWS KMS keys (DSSE-KMS)
	-  Server-side encryption with customer-provided keys (SSE-C)

- If objects in the **source bucket re not encrypted**, the replica objects in the destination bucket are encrypted by using the default encryption settings of the destination bucket.
- If objects in the source bucket are encrypted by using server-side encryption with Amazon S3 managed keys (SSE-S3), server-side encryption with AWS Key Management Service (AWS KMS) keys (SSE-KMS), or dual-layer server-side encryption with AWS KMS keys (DSSE-KMS), the replica objects in the destination bucket use the same type of encryption as the source objects. **The default encryption settings of the destination bucket are not used.**
- Amazon S3 Bucket Keys 
- -  SSE-C, SSE-S3, SSE-KMS, DSSE-KMS
- **SSE-C**
	- server-side encryption with customer-provided keys (SSE-C). You must provide an encryption key as part of your request, but you don't need to write any code to perform object encryption or decryption
	- When you retrieve an object, **you must provide the same encryption key** as part of your request
- **SSE - S3** 
	- Amazon S3 managed encryption keys (SSE-S3) - Default encryption where key encryption is managed by Amazon
- SSE-KMS - here key for encryption and decryption are managed by customer
- ![[S3 Bucket Key.png]]
	-  reduce the cost of Amazon S3 server-side encryption with AWS Key Management Service (AWS KMS) keys (SSE-KMS)
	- When you configure your bucket to use an S3 Bucket Key for SSE-KMS, AWS generates a **short-lived bucket-level key from** AWS KMS then temporarily keeps it in S3
	- Workloads that access millions or billions of objects encrypted with SSE-KMS can generate **large volumes of requests to** AWS KMS


##### Client Side Encryption
-  To encrypt your objects before you send them to Amazon S3, use the **Amazon S3 Encryption Client**
