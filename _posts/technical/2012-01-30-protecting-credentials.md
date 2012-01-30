---
layout: post
title: "Protecting your credentials from criminals"
who: chris
---

<style>
.indent {padding-left: 20px;}

</style>

<p> In my <a href="http://blog.onetimesecret.com/2012/01/25/good-passwords/">previous blog post</a>, 
I wrote about choosing good passwords. However, most hack attempts don't involve password hacking/guessing 
at all. Even dictionary attacks — which are far more common that brute force attacks — are not the 
most common way that criminals get at your account information and private data. In this blog post, 
I'll mention some of the more common attacks, and how you can protect yourself against them.</p>

<p>Throughout this post, I use the word <em>criminal</em> instead of <em>hacker</em> to distinguish between
the two senses of the word that <a href="http://en.wikipedia.org/wiki/Hacker_%28computer_security%29">hacker</a> 
has. In the media, hacker is synonymous with 'computer criminal' — the bad people who steal money from banks 
or who use computers to defraud people. In IT communities however, hackers are a sub-culture of software/hardware developers and 
enthusiasts who are simply interested in technology, software and security. The vast majority of them 
are not criminals, and in fact many of them spend their time trying to stop the criminal activity. 
Sometimes the good vs bad hackers are described as '<a href="http://en.wikipedia.org/wiki/White_hat_%28computer_security%29">white hat</a>' 
and '<a href="http://en.wikipedia.org/wiki/Black_hat">black hat</a>' hackers respectively. 
</p>


<h3>Phishing</h3>

<p class="indent">
The term '<a href="http://en.wikipedia.org/wiki/Phishing">phishing</a>' is a hacker term that comes 
from 'fishing', implying that there is a bait and that someone is waiting for a bite from a victim. 
This is because phishing attacks often involve sending a potential victim some sort of request or 
message, often forged or made to look like it is from some other individual or company. The 
'bait' is a message that is a call to action on the victims part, enticing them to give 
up some private information.
</p>
<p class="indent"> For example: they might send an email claiming to be your bank informing you that 
your account has been suspended temporarily. However, rather than just telling you to log into your
bank's web software (which is what a real notice from a bank would do), they instead provide a link
for you to click on (something that banks will never do) that supposedly is to the bank's website. 
Often unbeknownst to the user, this link doesn't go to the bank's website, but another website that
is made to look exactly like the bank in question. When you enter your username and password to login,
you end up giving them to the criminals instead of the bank. This usually isn't traceable either, because 
the server hosting the forged bank website is also often a victim of attack or defacement via some
sort of vulnerability in their website.
</p>

<p class="indent"> The best way to protect yourself from these sorts of attacks is twofold:</p>

<p class="indent"><strong>1.</strong> Never click on links in emails that go to sites that require
a username and a password. Instead, always type out the URL yourself, or use a trusted bookmark that
you have in your browser.</p>

<p class="indent"><strong>2.</strong> Never go to websites that require a username and password
that don't also use SSL. SSL protected sites are encrypted, which protects your credentials over 
the network (more on that below), but they also have a trust mechanism in them, so you can look
at the URL to be sure that's where you want to be. Any site that is at all valuable should use
SSL, and your browser will let you know that it is a secure connection. If ever your browser complains
about a 'certificate error', or something similar, you should immediately close the tab or window
with that website.
</p>

<p class="indent">If you do get a phishing type email, your best bet is to send it to your bank's
online fraud email address. Pretty much every bank has one these days, you can go to your bank's
website (by typing the URL into your browser's location bar directly) and it should be relatively
easy to find. Other than that, you should also delete the email in question.</p>

<h3>Trojans</h3>

<p class="indent">
Trojans are often mistaken as 'viruses', however they're very different things. In computer terms,
a virus is something that gets 'attached' to a benevolent piece of software and somehow exploits
a bug to propagate itself. A trojan on the other hand is malevolent software from the get-go — it's
designed and developed specifically to do something positive that the user wants while also 
doing something malicious that the end user probably didn't want or intend at all. The name of course, 
comes from the <a href="http://en.wikipedia.org/wiki/Trojan_Horse">mythical Greek story</a> about
a large wooden horse that allowed the Greeks to conquer the city of Troy. So, like the wooden
horse, trojans look benevolent from the outside, but are actually harmful and designed as a means
of attack.
</p>

<p class="indent">
The way trojans are used to get your credentials are often by installing key-stroke tracking software
on your computer. Once this is done, everything you type is logged and sporadically sent off to 
a malicious server somewhere where the data is collected and analyzed for specific types of patterns,
(credit card numbers, usernames and passwords) or used to gather private information (emails, chats
or other typed documents).
</p>

<p class="indent"> 
Protecting yourself from trojans is getting more difficult these days, since trojan-modified versions
of common shareware and freeware software available for download have been found on what were 
<a href="http://www.tomsguide.com/us/CNET-CBS-Malware-Trojan-Nmap,news-13410.html">previously 
thought of as very reputable sites</a>. The best way to protect yourself is to never download
software from unknown websites, and treat any executables emailed to you with extreme caution. With
very few exceptions, the best course of action is to delete the email and not click on anything inside it.
</p>

<h3>Honeypots and Network Sniffing</h3>

<p class="indent">
Another common way that criminals get your credentials is via 
<a href="http://en.wikipedia.org/wiki/Honeypot_%28computing%29">Honeypots</a>. Honeypots are often
used by white hat hackers as a tool to catch black hats and criminals in order to study their
methods in a relatively safe environment — this is often in a highly secured and segregated segment of 
a network, so that if the service is attacked and taken over, the criminals won't be able to
do any further damage. The term 'honeypot' comes from the idea of using a pot of honey to catch flies — 
you just leave it out there, and eventually the flies are all stuck in the pot.  
</p>

<p class="indent">
However, not all honeypots are run by good guys. Like a trojan, a honeypot is a tool, or service that 
seems beneficial, however it's end goal is definitely not. A very common black hat honeypot is
a 'free' wifi hot-spot. Since they are in control of the hotspot, all traffic is routed and controlled
by them. This means that they can give bogus <a href="http://en.wikipedia.org/wiki/Domain_Name_System">DNS 
responses</a> and therefore easily route you to forged/malicious websites even if you use your own
bookmarks or type URLs directly. Also, any traffic that isn't encrypted (http instead of https) can be 
spyed on and collected and analyzed. So passwords or sessions for popular sites that don't use SSL can
be <a href="http://en.wikipedia.org/wiki/Packet_analyzer">sniffed</a> and <a href="http://en.wikipedia.org/wiki/Session_hijacking">hijacked</a>, 
effectively giving the criminals control over your accounts.</p>

<p class="indent">The best way to protect yourself from this sort of attack is very similar to
the phishing techniques above. You should never connect to a wifi hotspot that isn't trusted,
and even if it is trusted, while you are using that you should never connect to sites that don't
use SSL for <strong>all</strong> of their communications. While not available to many people, the 
best way of all would be to use <a href="http://en.wikipedia.org/wiki/VPN">VPN</a> whenever you are 
on a public network, including all known/reputable wifi hotspots. Chances are, if you work for a
company that has a decent security policy and expects you to connect to their networks from home
or on the road, they do (or at least should) provide VPN connectivety. 
</p>








































