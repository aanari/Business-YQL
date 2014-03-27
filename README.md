# NAME

Business::YQL - YQL Perl interface for the Y! Query API

# VERSION

version 0.0003

# SYNOPSIS

    use Business::YQL;

    my $yql = Business::YQL->new;
    my $data = $yql->q('show tables');

    $data = $yql->query("insert into yahoo.y.ahoo.it (url) values ('http://google.com')");

# DESCRIPTION

This module provides a simple Perl interface (via JSON) to perform YQL queries.  You can test queries in Yahoo's developer console here: [http://developer.yahoo.com/yql/console](http://developer.yahoo.com/yql/console).

# METHODS

## new

Instantiates a new Business::YQL client object.  All parameters are optional.

    my $yql = Business::YQL->new(
        scheme => 'http',
        domain => 'query.yahooapis.com',
        version => 'v1',
        timeout => 10,
        retries => 3,
    );

__Parameters__

- \- `scheme`

    _Optional_&#10; &#8;

    The valid HTTP scheme for the URI builder.  Defaults to `http`.

- \- `domain`

    _Optional_&#10; &#8;

    The Yahoo API top-level domain to make API calls against.  Defaults to [query.yahooapis.com](http:/query.yahooapis.com).

- \- `version`

    _Optional_&#10; &#8;

    The Yahoo API version to use.  Defaults to `v1`.

- \- `timeout`

    _Optional_&#10; &#8;

    The maximum number of seconds to wait after submitting an HTTP request before timing out the response.  Defaults to `10` seconds.

- \- `retries`

    _Optional_&#10; &#8;

    The number of times to retry requests in cases when Yahoo returns a 5xx response.  Defaults to `3` attempts.

## q

Submits the YQL query, this method simply takes a string to send to Y! API, and returns the decoded JSON response n the form of a Perl object if the request was valid.

    q("SELECT * from geo.places WHERE text='SFO'")

# AUTHOR

Ali Anari <ali@anari.me>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2014 by Ali Anari.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
