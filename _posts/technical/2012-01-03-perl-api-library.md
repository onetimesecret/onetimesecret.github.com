---
layout: post
title: "New API client library: Perl"
who: delano
---

We now have a perl client library for our [API](https://onetimesecret.com/docs/api/) thanks to <a href="http://www.shoffle.com/">Kyle Dawkins</a>. The code is available on [Github](https://github.com/quile/OneTimeSecret) and [CPAN](http://search.cpan.org/~kyled/Net-OneTimeSecret-0.01/lib/Net/OneTimeSecret.pm). Here's an example:

{% highlight perl %}
use Net::OneTimeSecret;

$api = Net::OneTimeSecret->new( 'chris@onetimesecret.com', '4dc74a03fwr9aya5qur5wa8vavo4gih1hasj6181' );

$response = $api->shareSecret( "Jazz, jazz and more jazz." );
$secretKey = $response->{secret_key};

$retrievedMessage = $api->retrieveSecret( $secretKey );
print $retrievedMessage->{value};  #=> Jazz, jazz and more jazz.
{% endhighlight %}

*If you implement a client library in another language, let us know and we'll post about it here.*
