- you can share AWS KMS CMKs with another AWS account by adding to other account to the AWS KMS key policy
##### Automatic key rotation
- rotate every year, after May 2022, it rotates every three years
- won't delete old ones, until user deletes them
- track the rotation in cloudwatch and cloudtrail
- rotaion supports onlu symetric enrcyption KMS keys
- rotation is optional for customer managed key, but can be enable and disable at any time
- but it always rotate AWS managed keys
-  **KMS key should be created in the same region as the S3 bucket**
- 