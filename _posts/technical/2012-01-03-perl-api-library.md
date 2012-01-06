---
layout: post
title: "New API client library: Perl"
who: delano
---

We now have a perl client library for our [API](https://onetimesecret.com/docs/api/) thanks to <a href="http://www.shoffle.com/">Kyle Dawkins</a>. The code is available on [Github](https://github.com/quile/OneTimeSecret) and [CPAN](http://search.cpan.org/~kyled/Net-OneTimeSecret/lib/Net/OneTimeSecret.pm). Here's an example:

{% highlight perl %}
#!/usr/bin/env perl

use Net::OneTimeSecret;

# Note: replace these with yours in order for this to work!
my $customerId  = 'chris@onetimesecret.com';
my $testApiKey  = '4dc74a03fwr9aya5qur5wa8vavo4gih1hasj6181';

my $api = Net::OneTimeSecret->new( $customerId, $testApiKey );
my $result = $api->shareSecret( 'Jazz, jazz and more jazz.',
                   passphrase => 'thepassword',
                   recipient => 'kyle@shoffle.com',
                   ttl => 7200,
                 );
printf( "%s\n", $result->{secret_key} );

my $secret = $api->retrieveSecret( $result->{secret_key}, passphrase => "thepassword" );
printf( "%s\n", $secret->{value} );

{% endhighlight %}

*If you implement a client library in another language, let us know and we'll post about it here.*
