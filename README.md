# victor

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
- That joint information is commited under the proper year/month directory.
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
independent timestamping. 
Please kindly commit a signed announcement to that effect. 

Reference: Bruce Schneier, *Applied Cryptography*, 
1996 second edition, see esp. chapter 4.1.

