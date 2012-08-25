--- 
layout: post
tags: 
- Amazon Web Services
- IT
- S3
type: post
meta: 
  _edit_last: "1"
  _syntaxhighlighter_encoded: "1"
published: true
status: publish
title: Amazon S3 Virtual Hosting and Access Control
---
When you first come into <a title="Amazon Simple Storage Service (Amazon S3)" href="http://aws.amazon.com/s3/" target="_blank">Amazon S3</a>, <a href="https://console.aws.amazon.com/s3/home">AWS Management Console</a> provide a convent way to manage your s3 resource, including create bucket, upload object, view or download object.

But you must need another way to access your s3 objects, S3 provide a REST API let you access them, using HTTP protocol
<ol>
	<li>http://s3-us-west-1.amazonaws.com/bucknetname</li>
	<li>http://bucketname.s3.amazonaws.com</li>
	<li>http://img.example.com</li>
</ol>
<div>The first two way are build in with amazon s3, you need no configuration on them.</div>
<div>The 3rd way, which let you access your s3 object under your domain name, it's powerfull, but need a little config: First, create a bucket named as your domain name, such as "img.example.com", then configure your DNS name  "img.example.com" as a CNAME alias for "img.example.com.s3.amazonaws.com". then you can access your bucket which named "img.example.com" through http://img.example.com! Note:<span style="color: #ff0000;"> the bucket name must be the same as the CNAME</span></div>
You just know how to access your s3 resources, but before you can do that, you still need config who can access it. You may don't want everyone can do that, bcs this may cause you pay extra dollars :-(

Bucket Policies can do that! For example, you just want your website www.example.com but no ohters can use your picture hosted at s3, you can use the "aws:Referer" to do that:
[text]
{
	&quot;Version&quot;: &quot;2008-10-17&quot;,
	&quot;Id&quot;: &quot;your-uniqueness-id&quot;,
	&quot;Statement&quot;: [
		{
			&quot;Sid&quot;: &quot;Allow get requests referred by example.com&quot;,
			&quot;Effect&quot;: &quot;Allow&quot;,
			&quot;Principal&quot;: &quot;*&quot;,
			&quot;Action&quot;: &quot;s3:GetObject&quot;,
			&quot;Resource&quot;: &quot;arn:aws:s3:::img.example.com/*&quot;,
			&quot;Condition&quot;: {
				&quot;StringLike&quot;: {
					&quot;aws:Referer&quot;: &quot;http://www.example.com/*&quot;
				}
			}
		}
	]
}
[/text]
There are other key to use: "aws:SourceIp", "aws:UserAgent" etc. Read <a title="Element Descriptions" href="http://docs.amazonwebservices.com/AmazonS3/latest/dev/index.html?AccessPolicyLanguage_ElementDescriptions.html" target="_blank">Element Descriptions</a> for more.
<br />
------
Future Reading:
<a title="Making Requests" href="http://docs.amazonwebservices.com/AmazonS3/latest/dev/MakingRequests.html">How do I make requests</a>
<a title="Access Control" href="http://docs.amazonwebservices.com/AmazonS3/latest/dev/UsingAuthAccess.html">How do I manage access to my resources</a>
