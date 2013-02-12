---
layout: post
title: Copying server data from the command-line, safely
who: delano
---

All of times I've found myself in a situation where I need to get a little bit of data on to or off of a server somewhere. Copy & paste works in some cases but not always. Another option is a service like Pastebin but it's not cool for sensitive info like config files because even though you can easily forget to delete them when you're done.

That's where a one-time secret comes in: *a long, unique URI that only works once*.

## Installation ##

Our "official" tool is written in Ruby and available via [Rubygems.org](https://rubygems.org):

{% highlight text %}
$ sudo gem install onetime
{% endhighlight %}

You can also get it directly from the [github repo](https://github.com/onetimesecret/onetime-ruby/).

## Storing a message ##

You can create a secret by piping data from another command:

{% highlight text %}
$ history | onetime
https://onetimesecret.com/secret/c5lzg25xeze2ff2sotcf5dbi50k7go9
{% endhighlight %}

Directly from a file:

{% highlight text %}
$ </etc/nginx/nginx.conf onetime
https://onetimesecret.com/secret/2r13wmv03abrc2etmeaf4xzjr9xbu3f
{% endhighlight %}

Or by pasting or typing the content in at the prompt:

{% highlight text %}
$ onetime
Paste message here (hit control-D to continue):
Your password is: Two-spots-higher-622
^D
https://onetimesecret.com/secret/rvbkyzn6nylcjcaimot23oehja7zwuv
{% endhighlight %}

## Retrieving a message ##

{% highlight text %}
$ onetime get rvbkyzn6nylcjcaimot23oehja7zwuv
Your password is: Two-spots-higher-622
{% endhighlight %}

Or simply go to the onetimesecret.com URI and copy the message from there.

## Advanced options ##

Beyond the basic usage, there are some other features that might interest you as well.

#### Include a passphrase ####

For very sensitive data you will want to include a passphrase so that even if someone finds the secret link while it's still available, the won't be able to see the message unless they know the passphrase. We include the passphrase in the encryption key which guarantees that only you or the recipient can view the content.

{% highlight text %}
$ onetime generate -p 1234567890
https://onetimesecret.com/secret/2x7z9i5p4cg9mig890b7esqmv31d7hd
{% endhighlight %}

When the secret is retrieved, the passphrase must be identical.

{% highlight text %}
$ onetime get -p bogus 2x7z9i5p4cg9mig890b7esqmv31d7hd
Unknown secret
$ onetime get -p 1234567890 2x7z9i5p4cg9mig890b7esqmv31d7hd
RmUFWEzqVryR
{% endhighlight %}

#### Send the link via email ####
If you [sign up](https://onetimesecret.com/signup) for an account, you can also email the secret link directly to the recipient. You need to set two environment variables to tell `onetime` what account to use.

{% highlight text %}
$ export ONETIME_CUSTID=example@onetimesecret
$ export ONETIME_APIKEY=YOURSECRETKEY
$ onetime status
# Host: https://onetimesecret.com/api
# Account: example@onetimesecret.com
Service Status: nominal
{% endhighlight %}

Then you can send emails directly from the command-line:

{% highlight text %}
$ who | onetime -r delano@onetimesecret.com
# Secret link sent to: d******@onetimesecret.com
{% endhighlight %}

If you want to use this feature regularly, you'll want to set the `ONETIME_CUSTID` and `ONETIME_APIKEY` environment variables in your `~/.bashrc` file.

#### Output to json or yaml ####

You can specify a format using the `-f` option, like so:

{% highlight yaml %}
$ last | onetime -f yaml
---
custid: anon
metadata_key: g4blscedwb8hyxklzvb3q0m3jbbzhir
secret_key: hgar2i4s90kuflwfwr8nep7obng7t3
ttl: 604800
metadata_ttl: 604800
secret_ttl: 604800
state: new
updated: 1360704091
created: 1360704091
recipient: []
passphrase_required: false
{% endhighlight %}

## Use One-time Secret in your projects ##

If you want to use one-time secrets in your app or implement a tool in another language, [check out the API](https://onetimesecret.com/docs/api).

If you have any questions or feature requests, [let me know](https://onetimesecret.com/feedback).
