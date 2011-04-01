Pow: Zero-configuration Rack server for Mac OS X
================================================

**Pow is a zero-configuration Rack server for Mac OS X.** It makes
developing Rails and Rack applications _stupid easy_. You can install
it in ten seconds and have your first app up and running in under a
minute. No mucking around with `/etc/hosts`, no compiling Apache
modules, no editing configuration files or installing preference
panes. And running multiple apps with multiple versions of Ruby is
trivial.

How does it work? A few simple conventions eliminate the need for
tedious configuration. Pow runs as your user on an unprivileged port,
and includes both an HTTP and a DNS server. The installation process
sets up a firewall rule to forward incoming requests on port 80 to
Pow. It also sets up a system hook so that all DNS queries for a
special top-level domain (`.test`) resolve to your local machine.

To serve a Rack app, just symlink it into your `~/.pow`
directory. Let's say you're working on an app that lives in
`~/Projects/myapp`. You'd like to access it at
`http://myapp.test/`. Setting it up is as easy as:

    $ cd ~/.pow
    $ ln -s ~/Projects/myapp

That's it! The name of the symlink (`myapp`) determines the hostname
you use (`myapp.test`) to access the application it points to
(`~/Projects/myapp`).

## Installation

Pow requires Mac OS X version 10.6 or newer. To install or upgrade
Pow, just open a terminal and run this command:

    $ curl get.pow.cx | sh

You can [review the install script](http://get.pow.cx/) yourself
before running it, if you'd like. Always a good idea.

The installer unpacks the latest Pow version into
`~/Library/Application Support/Pow/Versions` and points the
`~/Library/Application Support/Pow/Current` symlink there. It also
installs
[launchd](http://developer.apple.com/library/mac/#documentation/Darwin/Reference/ManPages/man8/launchd.8.html)
scripts for your user (the Pow server itself) and for the system (to
set up the `ipfw` rule), if necessary. Then it boots the server.

**Note**: The firewall rule installed by Pow redirects all incoming
  traffic on port 80 to port 20559, where Pow runs. This means if you
  have another web server running on port 80, like the Apache that
  comes with Mac OS X, it will be inaccessible without either
  disabling the firewall rule or updating that server's configuration
  to listen on another port.

## Managing Applications

## Troubleshooting

## Contributing

## License

