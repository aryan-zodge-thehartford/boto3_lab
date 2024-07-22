# boto3_lab (Lab 0)
## Analysis Table
 
 ---

| Method | Purpose | Best Use Cases | Pros | Cons |
| :--- | :--- | :--- | :--- | :--- |
| **upload_file** | Uploads a file to an S3 bucket | Uploading large files; supports multipart upalods for large files. |Automatically handles multipart uploads for large files |Requires the file to be on the filesystem; less control over the uploads process |
| **upload_fileobj** | Uploads a file-like object to an S3 bucket | When you have a file-like object to an S3 bucket |Supports file-like opbjects; userful for streams and in-memory files | Less control over the upload process; may require manual handling of retries |
| **put_object** | Puts an object directly into an S3 bucket. | Simple and small file uploads; direct object manipulation | Direct and simple; useful for small files and metatdat control |No automatic handling of multipart uploads; no progress callbacks |
| **download_file** | Downloads a file from an S3 bucket to the filesystem | Downloading large files from S3 to the local filesystem |Handles multipart downloads; includes retries and progress callbacks |Requires a local filesystem; less control over the download process |
| **download_fileobj** | Downloads an S3 object to a file-like object | When you have a file-like object (like a file in-memory files) | Supports file-like objects; useful for streams and in-memory files | Less control over the download process; may require manual handling of retries |
| **get_object** | Retrieves an object fram an S3 bucket | Getting the contents of an S3 object along with its metadata |Returns the object data and metadata; useful for processing small files in memory | Not suitable for large files; no built-in handling for large object downloads |


## Real World Scenarios
**upload_file**: Best for large file uploads, such as uplaoding logs for media files from a local server to S3.

**upload_fileobj**: Ideal for streaming uploads directly from a web application to S3, where file are not stored on the local filesystem.

**put_object**: Suitable for quick uploads of small files or objects where you need direct control over the metadata.

**download_file**: Best for large file downloads, such as fetching backups or datasets from S3 to a local server

**download_fileobj**: Useful for applications that need to process files in-memory or stream data from S3.

**get_object**: Appropriate for retrieving small files or confiugartions stored in S3 for immediate use in an application.



## Reflection Questions