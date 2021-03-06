Working with Large Attachments
=

# Working with Large Attachments
#-

## Large Attachments and Timeouts
When a large attachment, or multiple attachments, are included within an email message the message parameter sent to the target website can become quite large.

When the content is large it can take considerable time to send this message to the target.
On a standard website you would place something like a progress bar within the page to show the user this process is occurring.
When CloudMailin delivers an email to your website there is no need to show any status but it is still important to consider the implications of receiving large files.

**Large requests can tie up the web server** for long periods of time and can often result in timeouts or unreachable errors as the server cannot cope with receiving that amount of data.
In addition it can prevent other requests from reaching the server.
If you experience issues like this when sending larger files it is worth considering having your files sent to S3, a system dedicated to working with files of this size.

## Sending Email Attachments to Amazon S3
#-

It is possible to configure CloudMailin to send message attachments to Amazons S3 as an email is received.
This can help reduce the overhead on the end server and allow you to easily save away the attachments sent by your customers.

In order to set up S3 attachments:

1. Log into your [address dashboard](http://cloudmailin.com/addresses) and choose the address you wish to manage.
2. Select add attachment store.
3. Enter your amazon S3 bucket name and an optional path to place before each file. In the format bucket_name/path_prefix.
4. Make sure you give write access for CloudMailin to your Amazon S3 bucket from the Amazon AWS dashboard.

In order for this to work you must give write access to your bucket to the following Amazon Canonical ID:

    AWS Canonical ID: 83fec836f8a832fae9c46e100739b635be3b3636d14887e1c7616e2dba1a88c0

Once this is configured correctly you will see an additional attachments parameter being passed with the content type, url and original file name of your attachments.
For more details about the attachment format see the documentation on the [HTTP Post Format](post_format#attachments).