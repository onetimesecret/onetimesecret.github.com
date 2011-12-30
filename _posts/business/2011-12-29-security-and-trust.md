---
layout: post
title: "Security, data protection and trust"
who: chris
---

<p>So, as I've mentioned in my previous post we have been getting a lot of
feedback from users, and we are listening. We've made changes to our UI and
features based on this feedback and we really appreciate it. Thanks again to 
everyone who has contacted us and helping us make One-Time Secret better.
</p>

<p>
There are a couple of questions that are asked fairly frequently that have to
do with usage, security and trust. People are rightfully leery of tursting third
party services with their sensitive data and want to know what steps we are taking
to protect it, and what they can do as well. Here are the three most popular questions
we get in this area:
</p>

<h4><em>Q: What do you do to keep the data from getting hacked/stolen?</em></h4>

<p>There are a number of things that we do to protect our servers and end-user data:</p>

<ul>
<li> We follow industry wide best practices. Delano and I are both web veterans, I've been 
a linux sysadmin for about 15 years now, Delano and I have managed hundreds of high profile, public
facing servers and web services.</li>
<li> We build our application, and the underlying infrastructure with security
in mind, using low privilege users for running services.</li>
<li> We're proactive in our use of restrictive firewalls and SELinux contexts, proper input 
validation and data segregation.</li>
<li> We follow PCI compliance rules, any data at rest (written to disk, etc.) is encrypted 
using well protected private keys.</li>
<li> We don't keep any data for longer than necessary. Backups of the database (all gpg encrypted)
are short lived and are for short term disaster recovery only.</li>
</ul>

<h4><em>Q: Is One-Time Secret safe enough for sensitive data like credit card numbers, etc.?</em></h4>

<p>Since one of our goals is to be <a href="http://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard">PCI compliant</a>,
by industry standards, we would be considered safe for such a purpose. However, their is another issue here, 
which is one of trust. How do you know we are who we say we are, and that we don't have other
motives? We try to mitigate against that by being transparent, and <a href="http://www.google.com/search?q=delano+mandelbaum">Delano</a>
and <a href="http://www.google.com/search?q=christopher+murtagh">I</a> easily identified on the net (I'm the 
<a href="http://www.google.com/search?q=christopher+murtagh+linux+-cricket">linux nerd</a>, not the 
<a href="http://www.google.com/search?q=chris+murtagh+cricket">Cricket player</a>). So,
we're openly putting our reputations on the line when we say we strive to keep your data safe. However, 
you should still proceed with caution - even the best intentions and best practices can still
lead to mistakes. There are steps that you can do to help protect your data:
</p>

<ul>
<li>Use encryption to transmit sensitive data, like <a href="http://www.gnupg.org/">GPG</a>, and send the passphrase
via another means (chat, phone, email, etc.).</li>
<li>Obfuscate the data so that it requires some other context to understand what it is. For example, for credit cards, you
could put some of the groups of numbers backwards and split it into multiple secrets. Let the recipient know how
to decipher the data via some other means (although, for truely sensitive data, GPG is still better).</li>
<li>Use the passphrase option when sending a message. We use that to encrypt the secret when storing it in the database, and we
don't store the passphrase at all. So, even if we wanted to read the data, we wouldn't be able to without the passphrase.</li>
<li>You could even use any combination of the above (or all), depending on how sensitive the data was.</li>
</ul>

<p>The important thing here is to understand the risks and to take reasonable measures to protect
yourself from them.</p>

<p>One other question or issue that has been raised by a handful of people:</p>

<h4><em>Q: Why don't you make it so that the user can't copy/paste the secret? Screenshots should be disabled too!</em></h4>

<p> Now, I think this question is a bit bizarre and betrays a misunderstanding of how HTML, browsers and 
the web work in general. There isn't any way that we could make secrets visable by humans and not
allow screen captures to work, not to mention that it would make the One-Time Secret much less useful and 
somewhat cumbersome if we could actually do this. The point of One-Time Secret is to allow users to pass data
to another party so that they can do something useful with it (read it, enter it into some other tool, use
etc.). Any mechanism where we used JavaScript to prevent copying and pasting is easily defeated by browser
plugins, and by doing so would give the sender a false sense of confidence that their data was safe in a
way that it really wasn't. If the data you need to send is so sensitive that a screenshot or copy/paste by
the intended recipient is too risky, then you should definitely not use One-Time Secret (or any other web based
service) to send it.</p>

