--- 
layout: post
title: amazon s3 virtual hosting and access control
category: tech
tags: 
- amazon web service
- s3
---
When you first come into [Amazon S3](http://aws.amazon.com/s3/), [AWS Management Console](https://console.aws.amazon.com/s3/home) provide a convent way to manage your s3 resource, including create bucket, upload object, view or download object.

But you must need another way to access your s3 objects, S3 provide a REST API let you access them, using HTTP protocol

* http://s3-us-west-1.amazonaws.com/bucknetname
* http://bucketname.s3.amazonaws.com
* http://img.example.com

The first two way are build in with amazon s3, you need no configuration on them.

The 3rd way, which let you access your s3 object under your domain name, it's powerfull, but need a little config: First, create a bucket named as your domain name, such as "img.example.com", then configure your DNS name  "img.example.com" as a CNAME alias for "img.example.com.s3.amazonaws.com". then you can access your bucket which named "img.example.com" through http://img.example.com! Note: **the bucket name must be the same as the CNAME** 

You just know how to access your s3 resources, but before you can do that, you still need config who can access it. You may don't want everyone can do that, bcs this may cause you pay extra dollars :-(

Bucket Policies can do that! For example, you just want your website www.example.com but no ohters can use your picture hosted at s3, you can use the "aws:Referer" to do that:

	{
		"Version": "2008-10-17",
		"Id": "your-uniqueness-id",
		"Statement": [
			{
				"Sid": "Allow get requests referred by example.com",
				"Effect": "Allow",
				"Principal": "*",
				"Action": "s3:GetObject",
				"Resource": "arn:aws:s3:::img.example.com/*",
				"Condition": {
					"StringLike": {
						"aws:Referer": "http://www.example.com/*"
					}
				}
			}
		]
	}

There are other key to use: "aws:SourceIp", "aws:UserAgent" etc. Read [Element Descriptions](http://docs.amazonwebservices.com/AmazonS3/latest/dev/index.html?AccessPolicyLanguage_ElementDescriptions.html) for more.

Future Reading:  
[How do I make requests](http://docs.amazonwebservices.com/AmazonS3/latest/dev/MakingRequests.html)  
[How do I manage access to my resources](http://docs.amazonwebservices.com/AmazonS3/latest/dev/UsingAuthAccess.html)
