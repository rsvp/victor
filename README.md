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

Alice has just finished her 404-page novel, 
and would like to register its date before sending 
it off to nine publishers for review. 
There is also a high-resolution image she would 
like to see on the front cover. 

```
I, Alice Example of Los Angeles, thereby record the 
SHA-256 digest of my novel, Unsolved Disappearances:
d98722c626307fb00e728ba2ff246b7dd91b932a1e872f19a42dedee3058cc8a
and a photo of my college friends:
f9c8cda5be4787626905f39e2d73ca4fe9615aeb607375683921595d3bb21cc0
on this day, Wed Nov  4 16:01:40 PST 2015.
```

She would like her notice to be posted on some reputable website, 
so she makes public the following: 
https://bitbucket.org/snippets/rsvp/bRxRA 
which will date Alice's notice independently of her stated claim. 

To strength the evidence of her authorship and completion date, 
she goes to Victor and makes a pull request of her original notice 
with added mention of the *Marker* site. 
Alice has been authenticated by GitHub, so Victor merges 
into the `2015/11` directory, something similar to: 
https://github.com/rsvp/victor/commit/ebe6e6b715089430017a03f2615722f1bb29da49

So now we have two more additional sources for the timeline: 
Victor's machine and the system time at a central repository. 
In fact, Alice has even stronger evidence because her commit is 
sandwiched among other authenticated users with an ordered trail of 
third-party markers publicly open for verification. 

The design of *git* as version control software places Alice's 
marker notice in a DAG, directed acyclic graph, 
with an unique immutable SHA-1 commit 
identifier: `ebe6e6b715089430017a03f2615722f1bb29da49` 
which will reveal not only various date sources but also 
the hash signatures of her original works. 
That identifier would serve as a superb reference code in 
Alice's communication with her prospective publishers. 

As a bonus, Alice had installed the post-commit hook 
found in Victor's bin -- which embedded her commit 
timestamp in another blockchain, Bitcoin -- free 
of charge:

```
 ::  hooks/post-commit: ebe6e6b715089430017a03f2615722f1bb29da49 to BLOCKCHAIN.
{"hash_sha256":"ebe6e6b715089430017a03f2615722f1bb29da49",
"created_at":"2015-11-05T01:10:15.648Z", 
"updated_at":"2015-11-05T01:10:15.648Z",
"submitted_at":null,"title":null}
 ::  http://www.originstamp.org/s/ebe6e6b715089430017a03f2615722f1bb29da49
[develop ebe6e6b] Add 2015-11-05-example.txt only as illustrative marker
```

Thus we have another verifiable public marker 
http://www.originstamp.org/s/ebe6e6b715089430017a03f2615722f1bb29da49 
which not only dated Alice's commit in real time, but also 
will report back hours later on the blocktime, the time 
of the confirmed Bitcoin transaction embedding her commit identifier. 

In effect, Alice's signed work is *permanently* on the Bitcoin blockchain. 
And just in case, for all the world to witness, a tweet is 
automatically posted (discretely) regarding this event: 
https://twitter.com/OriginStamp/status/662074416113799168 
which would constitute the seventh timestamp! 

Victor's protocol permits a timestamp to become trustworthy 
by the chained integrity of multiple independent sources of evidence 
which are publicly verifiable. 
Alice did not necessarily have to reveal the full contents 
of her novel to the world, but the means to authenticate 
it resides in one string preserved in many backed up 
copies of the open *victor* repository. 


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

