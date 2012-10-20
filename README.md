# Guard::Haml

Watches HAML files, compiles them to HTML on change.

[![Build Status](https://secure.travis-ci.org/manufaktor/guard-haml.png?branch=development)](http://travis-ci.org/manufaktor/guard-haml)

## My Extention
* Options
  1. :output => 'public'                   set output directory for compiled files
  2. :input => 'src'                       set input directory with haml files
  3. :run_at_start => true                 compile files when guard starts
  4. :notifications => true                send notifictions to Growl/libnotify/Notifu
  5. :haml_options => { :ugly => true }    pass options to the Haml engine
  6. :output_extension => "html/php"

## Install

As the gem name suggests this is a guard extension. Make sure you get [guard](https://github.com/guard/guard) first.

Install the gem:

    gem install guard-haml

Add it to your Gemfile if you're using bundler (you should)

    gem 'guard-haml'

Add a basic guard setup:

    guard init haml

## Options

If you want to change the output directory use the `output` option in your
Guardfile, e.g.:

    guard 'haml', :output => 'public' do
      watch %r{^src/.+(\.html\.haml)}
    end

This output is relative to the Guardfile.

If you maintain your haml files in a directory that should not be part of the output path, you can set the `input` option, e.g.:

    guard 'haml', :output => 'public', :input => 'src' do
      watch %r{^src/.+(\.html\.haml)}
    end

So when you edit a file `src/partials/_partial.html.haml`
it will be outputted in `public/partials/_partial.html` without the `src`.


If you want to compile haml files on guard start you can use `run_at_start` option.

    guard 'haml', :output => 'public', :input => 'src', :run_at_start => true do
      watch %r{^src/.+(\.html\.haml)}
    end

Also you can configure gaurd notification (to Growl/lib-notify/Notifu) by setting `notifications` option to `true`

    guard 'haml', :output => 'public', :input => 'src', :notifications => true do
      watch %r{^src/.+(\.html\.haml)}
    end

If you want to pass options to the Haml engine, you can set the `haml_options` option, e.g.:

    guard 'haml', :output => 'public', :input => 'src', :haml_options => { :ugly => true } do
      watch %r{^src/.+(\.html\.haml)}
    end

This will produce compressed HTML. See [Haml Reference](http://haml.info/docs/yardoc/file.HAML_REFERENCE.html#options) for more details.

## Development

* Source is hosted on [Github: guard-haml](https://github.com/manufaktor/guard-haml)
* Report issues/questions/feature requests on the [Github Issue tracker for guard-haml](https://github.com/manufaktor/guard-haml/issues)

Pull requests are welcome.
Specs are very welcome, make sure you support both ruby 1.8.7 and  ruby 1.9.2.
