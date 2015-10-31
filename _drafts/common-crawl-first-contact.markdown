---
layout: post
title:  "First time with common crawl"
categories: WebTechnologies commoncrawl java
comments: true
---

## Introduction

**[Commoncrawl](http://commoncrawl.org)** is like a copy or backup of the web. It stores the web page data responses so you can imagine the very very big 
size of the data. This data lives in the Amazon S3. The data is provided in three formats which are:

- **WARC Format**.  This format is the raw crawl data which includes the HTTP response (WARC-Type: response), how the information was requested (WARC-Type: request)
and metadata of the crawl process itself(WARC-Type: metadata).
- **WAT format**. This includes important metadata about the records stored in the WARC format. E.g if the response is HTML, the metadata includes the links listed
on the page.
- **WET format**. This includes only extracted plaintext.  

This data can be obtained via S3 or HTTP. e.g. here [april 2015 crawl archive](http://blog.commoncrawl.org/2015/05/april-2015-crawl-archive-available/) 
you can get the paths for the files, which are divided in segments. I just downloaded the following WARC file which size is approximately a gigabyte!:

https://aws-publicdatasets.s3.amazonaws.com/common-crawl/crawl-data/CC-MAIN-2015-18/segments/1429246633512.41/warc/CC-MAIN-20150417045713-00000-ip-10-235-10-82.ec2.internal.warc.gz

Due to my current project interests, what I will try to accomplish is to get a stream of a specific remote file and process the first ten records 
with a HTML response by printing it into the console. Additionally, with the help of common crawl index, I will retrieve a specific record.
This will be done with java language.

Before starting, much of what I learnt was from the common crawl [examples](https://github.com/commoncrawl/example-warc-java).


## 

- stream of a compressed file


gzip" is often also used to refer to the gzip file format, which is:

    a 10-byte header, containing a magic number (1f 8b), a version number and a timestamp
    optional extra headers, such as the original file name,
    a body, containing a DEFLATE-compressed payload
    an 8-byte footer, containing a CRC-32 checksum and the length of the original uncompressed data.

	https://en.wikipedia.org/wiki/Gzip
	
	
gzip cant be splittable. To access  specific part, is necessary first to create a index with the offsets.

deadlock while executing the parsers, because the size of buffer of the stream