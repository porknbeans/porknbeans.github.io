# porknbeans.github.io

This is the [Pork 'n' Beans website][www].

It is built using [Ruby][] and some [Rubygems][].

It's hosted on GitHub Pages, so it is "deployed" by simply committing to
the master branch of https://github.com/porknbeans/porknbeans.github.io.

All of the pages on the site are created as standard text files, editable in
any text editor. The site can be recreated with [Rake][], by running `rake` in
the directory.  Read the `Rakefile` for details on how. It's using [Tilt][], so
you may use loads of template and markup formats.

You can serve it locally with [Rack][] (`rackup`). See the `config.ru` for
details, or the description of `rake serve`.

In the future, it would be nice to add a commit hook that notifies a server that
can pull the changes, rebuild it, and re-commit it, so that changes could be
made directly on GitHub in the browser, and be reflected almost immediately.
Nice, but not too crucial.

[www]: http://porknbeans.github.io
[Ruby]: http://ruby-lang.org
[Rubygems]: http://rubygems.org
[Bundler]: http://bundler.io
[Tilt]: https://github.com/rtomayko/tilt
[Rack]: https://github.com/rack/rack
