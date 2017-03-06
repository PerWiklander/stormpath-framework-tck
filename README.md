#Stormpath is Joining Okta
We are incredibly excited to announce that [Stormpath is joining forces with Okta](https://stormpath.com/blog/stormpaths-new-path?utm_source=github&utm_medium=readme&utm-campaign=okta-announcement). Please visit [the Migration FAQs](https://stormpath.com/oktaplusstormpath?utm_source=github&utm_medium=readme&utm-campaign=okta-announcement) for a detailed look at what this means for Stormpath users.

We're available to answer all questions at [support@stormpath.com](mailto:support@stormpath.com).

# Stormpath Framework TCK

The Stormpath Framework TCK (Test Compatibility Kit) is a collection of HTTP-based integration tests that ensure a
Stormpath web framework integration supports all
[Stormpath Framework Specification](https://github.com/stormpath/stormpath-framework-spec) behavior.  The TCK uses
only HTTP(S) requests to ensure that they may execute against a web application written in any
programming language that uses any of the various Stormpath [integrations](https://docs.stormpath.com/home/)

This project is mostly used by the Stormpath SDK teams to ensure stability and consistent behavior for
our customers, especially those that use Stormpath across multiple programming languages. And for our own
development sanity :)  Comments, suggestions and/or contributions from the Open Source community are most welcome.

## Getting Started

1. If you haven't installed Maven already:

        brew install maven

2. Clone the project:

        git clone git@github.com:stormpath/stormpath-framework-tck.git

## Running tests

Fire up your web application under test.  For example, a Java project might do this:

    mvn jetty:run

And a node.js project might do this:

    node server.js

Once your web app is running, you can run the TCK against this webapp:

    cd stormpath-framework-tck
    mvn clean verify

This will run all tests against the targeted webapp.

To run a single suite, name it using the -Dtest flag:

    mvn clean verify -Dtest=LogoutIT

## Using Maven Profiles to Customize TCK Behavior

The TCK will attempt to interact with a web application accessible by default via `http://localhost:8080`.  You can
tell the TCK which type of application you are using by using a
[Maven Profile](http://maven.apache.org/guides/introduction/introduction-to-profiles.html) by specifying the `-P` flag:

    mvn clean verify -Pexpress

And this will assume a default base URI of `http://localhost:3000` (notice the changed port) since this is common for
node.js environments.

The currently supported profile names are:

* `express`
* `java`
* `laravel`

Additional profile names can be added if different language environments require custom settings.

## Test output as HTML

Besides viewing the output in the console, there's a nicer HTML format so you can view it through your browser:

```shell
open target/surefire-reports/index.html
```
