# JMAP-CLIENT

[![Join the chat at https://gitter.im/linagora/jmap-client](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/linagora/jmap-client?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://travis-ci.org/linagora/jmap-client.svg?branch=master)](https://travis-ci.org/linagora/jmap-client) [![Coverage Status](https://coveralls.io/repos/linagora/jmap-client/badge.svg?branch=master&service=github)](https://coveralls.io/github/linagora/jmap-client?branch=master)

This repository provides a JavaScript library to make requests against a JMAP server.
It is a client-side implementation of the [JMAP](http://jmap.io/spec.html) specification.
It is developed using **ES6** and transpiled to ES5 code using [babel.js](https://babeljs.io/).

Non-exhaustive list of features:
* Entities are modeled as JavaScript classes.
* Expose a *Client* class that you can use to send JMAP requests, using a fluent API.
* Uses Promises exclusively, and allows for pluggable Promise implementation.
* Allows for pluggable transports, with default support for node.js [request](https://github.com/request/request) and [jQuery](http://jquery.com/) in the browser.

## Usage

### Installation

The library is provided as a NPM or Bower packages, thus to install either use:

    npm install jmap-client

or

    bower install jmap-client

depending on your preferred package manager.

### Code

To use the library, create an instance of the *Client* class, then use its fluent API to send some JMAP requests:

    new jmap.Client(<your Transport>, <your PromiseProvider>)
        .withAPIUrl('https://jmap.my.server.com')
        .withAuthenticationToken('YourAuthenticationToken')
        .getMailboxes()
        .then((mailboxes) => {
            // Do something with the list of mailboxes
        }, (err) => {
            // An error occured
        });

Once you're familiar with the library, head on to the generated [API documentation](http://linagora.github.io/jmap-client/doc/api/) to see what methods are available.

## How to contribute

### 1. Clone the repository

    git clone https://ci.open-paas.org/stash/scm/olibs/jmap-client.git
    cd jmap-client

### 2. Install dependencies

    npm install

### 3. Compile the library and run the tests

    grunt

### 4. Code, execute tests then pull request !

More detailled instructions can be found in the [contributing section](./CONTRIBUTING.md).

## Release

If you are a maintainer of this project, here's how you can release a new version:

1. Checkout the _master_ branch and pull the latest changes from the remote repository
2. Run `grunt release` to do the release. A lot of things will happen but you'll eventually be back on the _master_ branch
3. Bump the version in _master_ to **NEXT_VERSION-dev** (replace _NEXT_VERSION_ by the supposed next version)

## License

[MIT](LICENSE)
