
## Star History

<a href="https://www.star-history.com/?repos=havaianasdestruido%2Fblaster&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=havaianasdestruido/blaster&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=havaianasdestruido/blaster&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=havaianasdestruido/blaster&type=date&legend=top-left" />
 </picture>
</a>

DECOMPILED SOURCE FOR MS RPC DCOM BLASTER WORM
<http://robertgraham.com/journal/030815-blaster.c>

This file contains source code for the "msblast.exe" worm
that was launched against the Internet on August 10, 2003.

This "source-code" was decompiled using "IDApro", an
"interactive disassembler". IDA is the most popular tool
for inspecting binary files. Note that IDA doesn't create
the source itself, but just helps understand the binary
so that source can be discovered.

Disclosing the source to blaster will not help blackhats.
The Blaster worm is not very good. However, it is
useful for whitehats to have a complete dissection of the 
worm.

BUFORD is the pseudonym I give to the blackhat hacker who 
wrote the worm. Many of my comments in the code talk about
conjectures I make about Buford.

This document contains many spelling and grammatical
errors. Also, while I have compiled it in order to see
how close I can get the binaries to match, I haven't
actually run it (and please don't compile/run it).


Why so slow?
The MS-RPC/DCOM vuln was the "worst-case-scenario" as far
as bugs go. It was the first "remote-hole" in the
"default-install" of a "desktop" operating system. Such
"remote-holes" in "servers" are the most popular for
hacking. Nimbda, CodeRed, and Slammer were all exploits
of "remote-holes" -- but since these bugs were in
optional components (web service, database) on desktops,
they didn't have the same reach as Blaster.


Blaster failed to take advantage of this fact. It was the
"best-case scenaro" for a worm. A normal worm would have
taken down the Internet for a few hours -- Blaster couldn't
have. For example, Buford (the programmer) didn't
acknowledge the TFTP packets, which meant that as more
congestion happened on the Internet, the less often Blaster
would successfully transfer itself to the new machine.
As a result, Blaster disabled the MS-RPC/DCOM service
on most machines rather than breaking into them, and it
didn't cause congestion problems on the Internet backbone.

Vulnerability references:
MS03-026 
<http://www.microsoft.com/technet/security/bulletin/MS03-026.asp>
CA-2003-16 
<http://www.cert.org/advisories/CA-2003-16.html>
CVE-2003-0352 
<http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2003-0352>
VU#568148 
<http://www.kb.cert.org/vuls/id/568148>
win-rpc-dcom-bo 
<http://xforce.iss.net/xforce/xfdb/12629>
Bugtraq-8205 
<http://www.securityfocus.com/bid/8205>
IAVA 2003-A-0011 
<http://infosec.navy.mil/pub/docs/advisories/FWIDS/IAVA_2003-A-001.doc>


Updates:

2003-08-29 
Jeffrey Lee Parson (aka. "teekid"), a Minnesota teen, was 
arrested for writing a "variant" of Blaster. All he did
was use the "upx" tool to decompress the worm, then did a 
"binary edit" to change strings, then recompressed the worm.
He also "infected" the worm with a "backdoor" program so that
he could later control the infected systems -- but this was
a backdoor/trojan he downloaded from the Internet, not one that
he created himself. Parson is not "Buford" -- he is not the
creator of Blaster.

2003-09-02
Parson's parents have gone on TV claiming that their son is not
a genius. This is interesting -- the prejudice that people have
is that hackers must be geniuses. This isn't true -- as this
analysis shows. The writer of Blaster himself was inexperienced
and simply combined components that other people had created.

2003-10-01
It seems clear now that Blaster (and possibly Nachi/Welchia)
are partially responsible for the northeast power blackout.
They disabled many of the control systems that could have been
used to stop the spread of the outage.

2003-11-05
Microsoft has announced a $250,000 bounty for the capture
and conviction of the creator of Blaster.
