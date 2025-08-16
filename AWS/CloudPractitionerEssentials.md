AWS Cloud Practitioner Notes
============================
* Notes created by Steven Stone (CiscoSteve42)

* Amazon Simple Storage Service (Amazon S3) can be used to store any type of data, and retrieve any amount of data from anywhere.

* In Amazon S3, any type of file, and any metadata that describes that file, is called an object. Objects are stored in S3 containers, called buckets.

* This solution uses an S3 bucket to host a static website. In Amazon S3, the static website can sustain any conceivable level of traffic, at a very modest cost, without the need to set up, monitor, scale, or manage any web servers.

* Along with an HTML file, files that support webpage functionality, such as client-side scripts and style sheets, are uploaded to the S3 bucket. Any S3 bucket can be configured to host a static website.

* When an S3 bucket is configured for website hosting, the bucket is assigned a URL. When requests are made to this URL, Amazon S3 returns the HTML file, known as the root object, that was set for the bucket.

* For others to access the S3 bucket, or specific objects in it, permissions must be configured to allow that access. A bucket policy can be created to configure these permissions.

* A bucket policy defines who can access the bucket and what type of operations can be performed. Bucket policies are written in JSON format.

* City residents visit the city web portal for beach wave information, which invokes a GET request from the portal to the URL of the static webpage. The initial root object is named index.html.

* The index.html root object in the S3 bucket can be renamed waves.html. The S3 bucket settings can be updated to use the renamed root object.
