---
layout: post
title:  "JSON Web Tokens: A Practical Guide For Authentication"
date:   2016-04-16 21:51:00 +0530
categories: Misc
---

UNDER CONSTRUCTION
==================

PLEASE TRY AGAIN LATER
======================

Technicially, JSON web tokens (pronounced "jot") "represent a set of claims as a JSON object that is encoded in a JWS and/or JWE structure". For more details found here http://self-issued.info/docs/draft-ietf-oauth-json-web-token.html, or skip that and continue reading this post, because life is too short to read RFCs.

Practically JWT's are uesd for authenticating  RESTful APIs requests. They serve as a better replacement/alternative to sessions as HTTP requests are supposed to be stateless. Sessions necciciates storing all the active user's state on the server which not only adds overhead in storing and fetching sessions, but also is a problem when scaling backend server horizontally.
JWT's on the other hand are self contained, i.e. a JWT has all the information needed to decoded it . Therefore it does need to be stored on server. Hence the server need not remember anything about any client as the HTTP request + JWT contains everything need to serve the right content to users.

Note that self contained nature of the JWT makes it a publicly readable (even a standalone javascript client can decode it).

So how are JWT used for Authetnication?
Here's the workflow in a graphic:
[[ TODO: Insert JWT request response work flow here]]
And here it is in text:
As soon as teh user log's in the app, a JWT containing users unique id is encoded in a JWT and signed with a SECERET key adn sent to the client on successfull login. 
Two things to note here: Sensitive information such as the user's password is not sent in the JWT as it could be easily compromised.
2nd: The JWT is SIGNED with a key that is known only to the server.

Clients after successfull login will capture this JWT and send it in the header with all subsiquent requests to the server. Server will 1) Verify and 2) Decode the JWT and if verified will get the decoded user id and server requests whatever the  logged in user wants. 
If someone tried to tamper witht the JWT from the client side server will reject it. 
For example, lets assume someone decoded and replace user1's userid in a valid legitimite JWT with USER2's user id, hoping to fool server into thinging user2 has logged in and making a request.
While User1 can replace user1's id with user2's id, s/he wont't be able to sign it because they dont have the SECERET which only the server knows.


TLDR: JWTs are encrypted and/or signed. JWT ensuer authentication by being readonly and non tamperable. 

[[ TODO: Techicals about jwt header payload signature ]]


<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
