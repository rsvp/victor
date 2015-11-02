# victor

[![Join the chat at https://gitter.im/rsvp/victor](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/rsvp/victor?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Victor, familiar name in cryptography to denote **VERIFIER**, 
serves to publicly timestamp hash fingerprints of files. 

People sometimes need to certify that a document existed on a 
particular date (e.g. for copyright or patent purposes). 
If the certification process can take place publicly 
that would certainly add veracity to the matter. 
GitHub can be used to perform as a trusted timestamping service. 

A git repository is designed in such a way that it is 
impossible to change a single bit of its content without 
that change becoming apparent in the commit identifiers 
(SHA-1). The explicit time of a commit is recorded by git, 
although it relies on the accuracy of the system's local clock. 

The **victor** repository shall be used as follows:

- User produces an one-way hash of a document, say, using SHA-256.
- That hash is posted at a reliable public site, 
  e.g. in a Bitbucket snippet or Twitter tweet with permalink.
- That joint information is committed under the proper year/month directory.
- Anyone can then *verify* the date and time of said hash. 

The virtue of this protocol is that the document itself 
is not stored within this repository. The user does not 
need to reveal the content of the document (*privacy*) 
since the hash digest will cryptographically suffice. 

Clearly the repository will not be large in size 
since the documents themselves are not stored 
(unless they serve to authenticate the timeline). 
The data is centrally backed up, but if this repository is 
distributed among many users, it can be securely reconstituted 
(not necessarily at GitHub). 

If a challenge occurs to a particular timestamp, one could 
in principle get testimony from originators of the previous and 
following documents: for the correct time must be sandwiched 
in-between them. Email addresses are used at GitHub to attribute 
work done in a repository. However, cross-validation 
using the URL addresses of where the hash codes were published 
should serve as evidence against collusion and faked timestamps. 

One may think of this repository as a collective union 
signing the public timeline of hash commits. 
The strict relative history of commits and git's cryptographic 
hash of those commits, together with open verification, 
are the essence of this project.
(This is far more refined than publishing your hash 
in a newspaper, a 20th century practice.)  

You can also contribute by periodically adding a hash of 
victor's last state to a blockchain for another source of 
independent timestamping. *New in v2:* every victor commit 
hash can be embedded into the **Bitcoin blockchain** 
automatically by incorporating the post-commit hook 
posted in `bin` -- free of charge! 


### Practical example

Following the protocol above, we date the following hash: 
[f1e616076764c468452169bbcf251355c397d1ee](https://github.com/rsvp/victor/blob/master/2015/10/2015-10-28-marker.txt) 
by committing a text file to **victor** under 
the proper year/month directory. 
Mention of a *marker* site is minimally useful to collaborate 
any claimed date and time (taking into account time zones). 
In our example, supplementary information has been included 
(helpful in a search of the repository): 

```
https://github.com/rsvp/victor
commit f1e616076764c468452169bbcf251355c397d1ee
Date:   Wed, 28 Oct 2015 15:01:43 -0700
Bump VERSION to v1.15.1028

Marker: https://bitbucket.org/snippets/rsvp/9qeyL
```

We have essentially added another timestamp to our commit by a 
third-party marker which can be verified by visiting that link. 
Thus we can definitively conclude that any hash registered thereafter 
would be dated 2015-10-28 or later. 
Prior entries would clearly have occurred on or before said date. 

The encoded timestamp from victor is 
[bdc5efb645764ec11cd6154d464c3269d47cb52a](https://github.com/rsvp/victor/commit/bdc5efb645764ec11cd6154d464c3269d47cb52a) 
which is the SHA-1 digest produced by git of a commit 
mentioning the hash to be registered plus any supplementary 
information inclusive of a time marker. 
Obviously any true clone of victor must contain 
the forementioned hash code [$ git log]. 

Given a series of such commits we are building a verifiable 
timeline built by diverse people with an ordered trail of 
authenticity provided by open markers on the network and 
the design of the git version control software. 


### References

- Trusted timestamping: https://en.wikipedia.org/wiki/Trusted_timestamping 
  see esp. [ANSI ASC X9.95 Standard](https://en.wikipedia.org/wiki/ANSI_ASC_X9.95_Standard) 
  and [Linked timestamping](https://en.wikipedia.org/wiki/Linked_timestamping). 

- Bela Gipp, N. Meuschke, and A. Gernandt. "Decentralized Trusted Timestamping 
  using the Crypto Currency Bitcoin," in *Proceedings of the iSchools iConference*, 
  Newport Beach, CA, USA, 
  [March 2015](http://www.gipp.com/wp-content/papercite-data/pdf/gipp15a.pdf) 
  or [arXiv:1502.04015 cs.CR](http://arxiv.org/abs/1502.04015) 
  [implemented in victor v2 post-commit hook]. 

- Bruce Schneier, *Applied Cryptography*, 1996 second edition, see esp. chapter 4.1.


### Appendix 1: Standards

Timestamps based on the X9.95 standard can be used to provide [*victor* comments]:

- Authenticity: trusted, non-refutable time when data was digitally signed. 
  [*victor presumes GitHub and markers use trusted time sources, e.g. NIST. 
  Note that victor does not hash or check the original document itself, 
  that's the committer's responsibility.*] 

- Integrity: protection of the timestamp from tampering without detection. 
  [*victor relies on the git's hash tree structure for integrity.*]

- Timeliness: proof that the time of the digital signature was the actual time. 
  [*victor timeline provides excellent approximation.*] 

- Evidentiary trail of authenticity. 
  [*A document's hash and a time marker jointly produces another hash, 
  git's commit identifier. Has the history of git commits been tested 
  in court for legal sufficiency?*] 

"**Linked timestamping** creates tokens [*markers*] 
which are dependent on each other, entangled into some 
authenticated data structure [*git hash tree* by GitHub users]. 
Later modification of issued timestamps would invalidate this structure. 
Temporal order of issued timestamps is also protected by this data structure, 
making backdating of the issued timestamps impossible, 
even by the issuing server itself." 

Summary: **The issued timestamps from *victor* are in fact the 
git SHA-1 commit identifiers. By examining the git log, 
the hash or signature of the original document can be recovered 
along with verifiable time parameters.**

