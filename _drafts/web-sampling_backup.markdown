---
layout: post
title:  "Web Sampling"
categories: WebTechnologies sampling
comments: true
---

> The sample size is the number of patients or other experimental units included in a study, and determining the sample size required to answer the research question is one of the first steps in designing a study. 


http://ndt.oxfordjournals.org/content/25/5/1388.long


> The confidence level is the amount of uncertainty you can tolerate. Suppose that you have 20 yes-no questions in your survey. With a confidence level of 95%, you would expect that for one of the questions (1 in 20), the percentage of people who answer yes would be more than the margin of error away from the true answer. The true answer is the percentage you would get if you exhaustively interviewed everyone.
> Higher confidence level requires a larger sample size.

http://www.raosoft.com/samplesize.html


The confidence interval (also called margin of error) is the plus-or-minus figure usually reported in newspaper or television opinion poll results. For example, if you use a confidence interval of 4 and 47% percent of your sample picks an answer you can be "sure" that if you had asked the question of the entire relevant population between 43% (47-4) and 51% (47+4) would have picked that answer.

The confidence level tells you how sure you can be. It is expressed as a percentage and represents how often the true percentage of the population who would pick an answer lies within the confidence interval. The 95% confidence level means you can be 95% certain; the 99% confidence level means you can be 99% certain. Most researchers use the 95% confidence level.

How many people are there in the group your sample represents? This may be the number of people in a city you are studying, the number of people who buy new cars, etc. Often you may not know the exact population size. This is not a problem. The mathematics of probability proves the size of the population is irrelevant unless the size of the sample exceeds a few percent of the total population you are examining. This means that a sample of 500 people is equally useful in examining the opinions of a state of 15,000,000 as it would a city of 100,000. For this reason, The Survey System ignores the population size when it is "large" or unknown. Population size is only likely to be a factor when you work with a relatively small and known group of people (e.g., the members of an association). 

http://www.surveysystem.com/sscalc.htm#one

This Markov process loosely captures the behavior of a typical
Internet user

http://www.cse.wustl.edu/~bjuba/papers/anomaly_detection.pdf


A memoryless random walk on the web graph is a
Markovian chain that visits a sequence of nodes where the
transitions between nodes depend only on the last node of the 
walk and not on earlier nodes. In a Markov chain on the web
graph states correspond to web pages, i.e. the nodes on the web graph, and each visit to a
node results in one step of the random walk. 

http://arxiv.org/pdf/0902.1604v1.pdf




1. Simple approach

Use a calculator like https://www.surveymonkey.com/mp/sample-size-calculator/ which are based on normal distribution and obtain a sample size. e.g. 
with a confidence level 99% and error 1, the sample size needed is 16641. Therefore a 16641 random records should be obtained from CC.
(I don't know if what I am saying is totally correct).Somehow obtain the url or offset from the crawl index randomly. 
The new common crawl index CC index (https://github.com/ikreymer/cc-index-server) (http://index.commoncrawl.org/) 
has a ZipNum Sharded CDX format and there 
is a framework in python pywb (https://github.com/ikreymer/pywb) that allows to manipulate these CDX files and also provides
an API for querying with URL's. The index contains the information (CC file URL, compressed offset, lenght) necessary to obtain
a particular CC record.

I am thinking that maybe an CDX (index) record can be obtained randomly from the CC index and with the offset obtain the CC record.

2. Page rank (Anomaly detectors paper)

Use page rank as distribution model and do a random walk (Markovian chain) as they do. This random walk leans towards to the 
Page rank distribution with the idea that the sampling will be more real compared to a normal user browsing. They used an older 
index (2012)and it seems there is no more support or willing to update it( https://github.com/trivio/common_crawl_index/issues/23 )
However I think the same idea can be done with the new CC index.

With this approach we need also to access randomly to a index record plus query the index with a retrieved URL 
and extract the links of a html so we can follow the random walk.

Therefore I am trying to figure out how to access a record randomly from the index. This will need to understand a bit the python code 
though there is a library in Java (https://github.com/iipc/webarchive-commons) that could also manipulate a CDX file.

Another thing, this CC index is not public, so I cannot download it without an amazon account. I was about to get my account but I prefered
to continue experimenting with CDX examples.

Regarding to the sampling size, I have been reading but still I don't know how to calculate the size yet(the first approach I stated is 
more intended for surveys, I think). As you can see I am bit lost here. 

I will appreciate any comment.

tools for the below server
https://github.com/ikreymer/pywb

For searching URL 
https://github.com/ikreymer/cc-index-server


ZipNum Sharded CDX is the format the new crawl index use

https://github.com/ikreymer/pywb/wiki/CDX-Index-Format


How the CC index is built
https://github.com/ikreymer/webarchive-indexing#building-a-local-cluster
http://aaron.blog.archive.org/2013/05/28/zipnum-and-cdx-cluster-merging/

python build_local_zipnum.py /home/jose/Downloads/ -s 25 /home/jose/Downloads/*.cdx

CDX Format
https://archive.org/web/researcher/cdx_file_format.php

CC index is built using the:
https://github.com/ikreymer/webarchive-indexing
Each reducer outputs the secondary index (one line per 3000 CDX lines), and creates a gzip file of the actual cdx lines as side-effect. Thus for each reducer, 0..N the following files are created.

    part-N - plain text secondary index
    cdx-N.gz - gzipped cdx index, concatenated chunks of X (usually 3000) CDX lines in each chunk.

	http://archive-access.sourceforge.net/warc/warc_file_format.txt

The common crawl Index is generated per each common crawl data set(collection) which are generated in a monthly basis. The format of the index is called ZipNum Sharded CDX.
This divides the complete index into several blocks(called shards) of indexes(commonly 3000 records). These shards are spread over multiple compressed files (part-file). 
For each of these part-files exists a "second index" that contains the start offset and length of every block. 

	
Common crawl Sampling algorithm


recordsToGetPerIndexFile(secondIndexFile,numberOfRecords) = getFileSampleWithRepeatedElements(indexCollection)

for each secondIndexFile,numberOfRecords in recordsToGetPerIndexFile:
	recordsPerShard(shard,numberOfRecordsPerShard) = getShardSampleWithRepeatedElements(secondIndexFile,numberOfRecords)
	for each shard,numberOfRecordsPerShard in recordsPerShard:
		sample.add(getRandomRecords(shard,numberOfRecordsPerShard))
	end
end




