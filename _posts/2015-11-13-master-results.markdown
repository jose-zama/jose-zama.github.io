---
layout: post
section-type: post
title:  "Results of my MSc"
category: Career
comments: true
---

So, the results of the dissertation have been released. I was very happy when I saw my mark. And not only happy, very impressive because
I was not expecting a very good mark. After all the exhaustive work of more than 12 hours everyday at the school, the reward totally worth it.
I got the distinction and very good feedback from my supervisor and the other always unknown revisor. Actually I was afraid of the latter, who 
was very strict with my progress report and gave me a very low mark. Never mind, the end was a happy end. I really appreciate all the guidance
and support of my supervisor [Bijan Parsia](in my progress report). He is amazing. Although I have to confess that sometimes I did not understand 
at all what the hell he was saying(plus I am not native English speaker as you can see). 

Well then, my dissertation title is *A testing strategy for HTML5 parsers* consisted in testing several HTML5 parsers in order to measure 7
the level of compliance with relation to the HTML5 specification.(**NOTE** there are two specifications: [W3C](http://www.w3.org/TR/html5/syntax.html#parsing) 
and [WHATWG](https://html.spec.whatwg.org/multipage/syntax.html#parsing) and according to my HTML5 survey, WHATWG is more popular). By and a large,
a Java implementation of the HTML5 algorithm  was built to understand the specification and then a test harness was designed and built to test 
several HTML5 parsers. This test harness was based in a N-version diversity in which the outputs of different HTML5 parsers were compared. As they follow
the HTML5 specification, the outputs should be exactly the same. Any difference or disagreement might represent a bug in one of the parsers. To run this 
test harness, samples from Common Crawl were taken as input and also the HTML5lib test suite. 

Following is a table showing the probability of convergence of the parsers tested in this project. The second column shows the results with relation to
a sample from the Common crawl dataset from May 2015, and the third from July 2015. As you can see *validatorNU* and *parse5* shows more convergence. This means
that these parsers are very robust with relation to the HTML5 specification. On the other side, do not expect too much from *Jsoup*, which shows that it will
probably give unexpected outputs, if you want to be compliant to the standards.
  
|-----------------+------------+-----------------|
| Parser | May 2015 (%) | July 2015 (%)| 
|---------------|----:+---:|
|validatorNU	|99.8 |99.9|
|---------------+-----+----|
|parser5 		|99.8 |99.9|
|---------------+-----+----|
|html5lib 		|82.0 |79.0|
|---------------+-----+----|
|MScParser 		|79.1 |77.6|
|---------------+-----+----|
|AngleSharp 	|78.0 |79.1|
|---------------+-----+----|
|Jsoup 			|4.9  |4.3 |
|---------------+-----+----|

If you are interested in taking a look to my dissertation, click [here](/assets/Dissertation_JoseZamudio_9572928.pdf) and let me know any comment.

