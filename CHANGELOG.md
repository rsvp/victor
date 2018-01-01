## CHANGE LOG 

*Each file in this project generally has a detailed change log contained 
within itself. This file simply gives a grand overview of such details 
and the annotations in the commits and tags.*


### 2018-01-01  (tag: v2.18.0101)

README.md: Bela Gipp on Bitcoin blockchain trusted timestamping, 
see arxiv.org/abs/1502.04015

Add bin/signvictor to sign commit timestamps of a repo.
Output can be published publicly for another piece
of evidence supporting the timeline of events.

Add 2015-11-02-marker.txt as output from signvictor.
So the full commit history up to v2.15.1101
is hashed as signed message with sha256 at
https://rsvp.quora.com/victor-v2-15-1101

v2 Practical example for README.md using Alice's novel.
Obviously she is fictional, but the dates and markers are real.

Add 2018/01/2018-01-01-marker.txt via signvictor.

Add .github directory for templates and info:

- new file:   .github/CODE_OF_CONDUCT.md
- new file:   .github/CONTRIBUTING.md
- new file:   .github/ISSUE_TEMPLATE.md
- new file:   .github/PULL_REQUEST_TEMPLATE.md


### 2015-11-01  (tag: v2.15.1101)


### 2015-10-31 

Add bin/proofexist to register hash or get time parameters

Uses API at https://proofofexistence.com/developers.
Hash embed into Bitcoin blockchain costs at least 5 mBTC.


### 2015-10-30 

Add bin/post-commit_OriginStamp for your .git/hooks

After a git commit its hash identifier will be
appended to the Bitcoin blockchain using the
API developed by OriginStamp.com

Add 2015/10/2015-10-31-marker.txt for Bitcoin BLOCKCHAIN

Successful TEST for post-commit using OriginStamp.org API
It is a simple curl post, and it was really free!
Immediate service is available for $1.00 at their site,
see Marker. Wait few hours for official Bitcoin confirmation.


### 2015-10-27 

Initial commit. Add LICENSE.md just in case: revised BSD.


