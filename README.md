Heroku buildpack: curl with HTTP/2 support
==========================================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) that shadows the system-provided `curl` executable and `libcurl` with a custom built version, most notably for its HTTP/2 support – provided by nghttp2.

It is not meant to be used standalone, just as an extra layer before the actual language buildpack.

Usage
-----

See Heroku's documentation on [multiple buildpacks](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app).

Example for a Vapor app:

    $ heroku buildpacks:set https://github.com/vapor-community/heroku-buildpack.git
    $ heroku buildpacks:add https://github.com/vzsg/heroku-buildpack-curl-http2.git --index 1
    $ git push heroku master
    ...

You can verify the installation using the following command:

    $ heroku run "curl --version"
