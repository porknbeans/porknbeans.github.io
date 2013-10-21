# porknbeans.github.io

This is the [Pork 'n' Beans website][www].

It is built using [Ruby][] and some [Rubygems][]. You should also install
[sass][] for the CSS, [Redcarpet][] for the markdown, and [CoffeeScript][] for
the JavaScript.

- `rake` or `rake build` updates the website locally
- `rake myfile.html` updates myfile.html (can be any HTML, CSS or JS target)
- `rake clean` delets all the HTML, CSS and JS files
- `rake serve` starts a server for you to test the site.

It's hosted on GitHub Pages, so it is "deployed" by simply committing to
the master branch of https://github.com/porknbeans/porknbeans.github.io.

[www]: http://porknbeans.github.io
[Ruby]: http://ruby-lang.org
[Rubygems]: http://rubygems.org
[Bundler]: http://bundler.io
[sass]: http://sass-lang.com
[Redcarpet]: https://github.com/vmg/redcarpet
[CoffeeScript]: http://github.com/josh/ruby-coffee-script
