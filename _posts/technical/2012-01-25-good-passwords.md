---
layout: post
title: "'Good' vs 'Strong' passwords"
who: chris
---

<p>One of my pet peeves about security are people who advocate for 'strong' passwords. Everyone knows these people,
they're the tech support person who tells you your password <strong>must</strong> have a minimum number of characters
that you only use when censoring expletives. Even worse, some of them use a random password generator to assign a 
password to you that you're unable to change. The argument for this is that if you have a wider range of characters
in your password, you have greater <a href="http://en.wikipedia.org/wiki/Password_strength#Entropy_as_a_measure_of_password_strength">
<em>entropy</em></a> and therefore it is harder for your password to be hacked. Now, while there is
some truth to that, there are numerous flaws in the logic when using it to determine a good security policy:
</p>

<h3>1. Most hack attempts are not 'guesses'</h3>

<p style="padding-left: 20px;"> High entropy is great when there is a <em><a href="http://en.wikipedia.org/wiki/Brute_force_attack">brute force</a></em> 
attempt to gain access. This is where the attacker uses an automated mechanism to repeatedly try different password 
combinations to try 'guess' your password. In the vast majority of cases however, this attempt is never used because 
it requires a lot of guesses to have a statistically significant chance of succeeding. For attacks across networks (ssh, 
ftp, http/web), the latency in the network itself, along with simple measures on the service to limit guess attempts 
means that this sort of brute force attack has no significant chance of succeeding. If the hacker has access to the encrypted
password file or database however, then this strategy gains a vastly higher probability of success, since they
can attempt this 'offline' (that is, on their own system) and the only limiting factor is their own
computing resources — the network and service limitations are no longer a factor at all.</p>

<h3>2. Most remote hack attempts are dictionary based</h3>

<p style="padding-left: 20px;"> So, a common question to #1 above is: "<em>If remote guessing hack attempts are unlikely to succeed, why are there 
all sorts of authorization failures in my logs?</em>" The answer is that, while there may be some very clueless 
hackers attempting 'guesses', they should just be considered background noise. The vast majority of them are not 
doing this, they're using something called a <em><a href="http://en.wikipedia.org/wiki/Dictionary_attack">dictionary 
attack</a></em>. What this means is that they have a list of very common usernames (<em>root, admin, dave, jane, etc.</em>) 
and another list of very common passwords (<em>abc123, qwerty, 1q2w3e4r, password, 123456, etc. </em> - yes, people do use 
these passwords with surprising regularity!). Then they cycle through their usernames and passwords until they get 
a hit. While the success rate is still very low, it's nowhere near as low as it should be. This is why you should 
<em>never</em> use these sorts of passwords. Also, if your name is 'dave' or 'jane' you might want to change that. :-)
</p>

<h3>3. Good security is a complex problem </h3>

<p style="padding-left: 20px;"> One thing that 'strong' password advocates forget is that there are a number of factors to consider when
determining a good security policy. Simply mandating 'strong' passwords to users in a draconian fashion ignores 
something very important: people have bad memories and generally aren't concerned about security. So, if they're 
given a password like '6dRre%!_0dc8' (yes, I've dealt with sysadmins who required these sorts of passwords), they're 
going to have to do something to remember this beast. Most of the time this means either typing it in a text file on 
their computer, or writing it down on a sticky note next to their desk. The text file gets into backups, and
is distributed around the net when they email it to themselves and the sticky note is often in plain sight! This 
becomes the security hole, and the policy to make security stronger just had a direct hand in making it weaker.
</p>


<h4>So, what exactly is a <em>good</em> password, and how is it different or better than simply a <em>strong</em> password?</h4>

<p> A good password is one that still has a minimum amount of entropy (simply put, diversity and lots of it), but equally
importantly, it is something that you are able to remember without any sort of impossible mental games that only
the kid who can solve any Rubik's 9x9 cube in 30 seconds can do. <a href="http://en.wikipedia.org/wiki/Password_strength">This 
Wikipedia article on Password Strength</a> does cover the entropy part quite well, although probably in a way where 
most people would not understand it or care to read it. However, it also makes some suggestions that are just plain wrong, such as:
</p>

<p style="padding-left: 20px;"><em>Generating passwords randomly where feasible</em></p>

<p> This is just simply bad advice. While there may be some tiny statistical advantage to 'random' passwords — due to 
the distribution of letters used in most passwords — this advantage is completely lost due to #3 above. Humans are not 
good at remembering random passwords, so assigning them is a bad practice. It just makes things difficult for them
and they will do something that will end up being worse.</p>

<p>Here are some examples of what I would call a <em>good</em> passwords:<p>

<p style="padding-left: 20px;"><em>99cakes?Yum.Yesplease!</em></p>

<p style="padding-left: 20px;"><em>The5thElement,Ilovedthatmovie!</em></p>


<p>What makes these passwords good? Well, they have a lot of entropy — upper case and lower case letters, punctuation
and numbers — and they're something that I can remember easily. Who wouldn't like 99 cakes? (ignoring health concerns
of course!), and The 5th Element was awesome! Now, ironically, these are now <strong>bad</strong> passwords, because 
they were suggested as a good ones on a blog with a focus on security! So, don't use them, but instead, use something 
similar that is meaningful for you. You try a couple of them, and use 
<a href="https://www.microsoft.com/security/pc-security/password-checker.aspx">Microsoft's web tool that checks password
strength</a> to see if they hold up.
</p>

