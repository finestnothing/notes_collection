# upload_to_s3

## Purpose

upload a file from dbfs to an s3 bucket
Only supports uploading file of 1 type, not csv AND excel in the same integration

## Inputs

- #file_path - Path of File to Write
	- #e_file_path - Path of encrypted file
- #file_name - Name of File to write
	- #e_file_name - Name of encrypted file
- #file_type - File Type to Get File
- #s3_bucket - Bucket to write file to
- #s3_file_path - Path to write file to
- #s3_file_name - Name to write file to

## Outputs

File(s) copied to s3 bucket
