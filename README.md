# Customizable Jetty service for dotCloud

This is a re-implementation of the [dotCloud](http://www.dotcloud.com/) [java service](http://docs.dotcloud.com/services/java/), using the new custom build API.

## What?

You want this if:

- you use dotCloud
- you deploy Java apps
- you want to customize Jetty in every possible way

## How?

To test this, use the good old "git clone / dotcloud push" method:

    git clone git://github.com/dotcloud/jetty-on-dotcloud.git
    dotcloud push mylittlejetty jetty-on-dotcloud

To deploy your own application, drop your WAR file(s) in the "webapps" directory.

Don't forget to do one of the following:

- git add+commit the WAR file (since by default, the dotcloud CLI will "git push"),
- ``dotcloud push`` with the ``--all`` flag (will force the use of rsync over git),
- rm the ``.git`` directory (the CLI will gracefully fallback on rsync).

## Troubleshooting

If it doesn't work, try ``dotcloud logs`` to see what's happening.

## Scaling

Horizontal scaling will work as expected. If you apply vertical scaling, you should probably edit ``jetty/run`` to customize the JVM parameters and specify an appropriate heap size.

## Warning

This recipe is based on dotCloud "custom build API". This API is in beta, and changes quite often; so this recipe will probably evolve over time. 
