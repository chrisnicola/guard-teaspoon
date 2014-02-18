Guard Teaspoon
==============
[![Gem Version](https://badge.fury.io/rb/guard-teaspoon.png)](http://badge.fury.io/rb/guard-teaspoon)
[![Dependency Status](https://gemnasium.com/modeset/guard-teaspoon.png)](https://gemnasium.com/modeset/guard-teaspoon)
[![Build Status](https://travis-ci.org/modeset/guard-teaspoon.png?branch=master)](https://travis-ci.org/modeset/guard-teaspoon)
[![Code Climate](https://codeclimate.com/github/modeset/guard-teaspoon.png)](https://codeclimate.com/github/modeset/guard-teaspoon)
[![Coverage Status](https://coveralls.io/repos/modeset/guard-teaspoon/badge.png?branch=master)](https://coveralls.io/r/modeset/guard-teaspoon?branch=master)

Guard-Teaspoon allows you to run [Teaspoon](https://github.com/modeset/teaspoon) using [Guard](https://github.com/guard/guard).

Teaspoon is a Javascript test runner built on top of Rails. It can run tests in the browser, or headlessly using PhantomJS or with Selenium WebDriver. We recommend you check out the [installation steps for Teaspoon](https://github.com/modeset/teaspoon#installation), and [read about configuration](https://github.com/modeset/teaspoon#configuration).

With Guard-Teaspoon you can start up Guard, make changes to your tests or implementation files, and the specs will be run automatically using Teaspoon. It behaves very similarly to guard-rspec.

This project is still experimental...


## Developer Notice

This project will be getting attention shortly, but it will currently be broken (I assume) with Teaspoon 0.8.

The version of guard-teaspoon will be bumped up to 0.8 as well and those will stay in sync from now on so that it's clear which versions work together well. It's an oversight that shouldn've been corrected earlier.

This project will transition away from being experiemental and will get more attention.


## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [Configuring Guard](#configuring-guard)


## Installation

Add it to your Gemfile. Like Teaspoon, in most cases you'll want to restrict it to the `:asset`, or `:development, :test` groups.

```ruby
group :assets do
  gem "teaspoon"
  gem "guard-teaspoon"
end
```

Install Teaspoon using the install generator.

```
rails generate teaspoon:install
```

Generate the Guardfile that includes the standard Guard-Teaspoon template.

```
bundle exec guard init teaspoon
```


## Usage

Start Guard.

```
bundle exec guard start
```

Make changes to your javascript specs or implementation files and the appropriate tests will run.


## Configuring Guard

In general this isn't very complicated, but if you have multiple suites setup in Teaspoon this can get a little complicated -- there's an expectation that you understand what you're doing in regards to using Guard.

The default Guardfile will watch for any file changes within your `app/assets/javascripts` path and will attempt to resolve those file to a spec. If you're using QUnit, you can change this to be _test instead of _spec, or use js.coffee or coffee for file extensions, and you can use a more advanced regexp for other needs.

Guardfile
```ruby
guard :teaspoon do
  watch(%r{^app/assets/javascripts/(.+).js}) { |m| "#{m[1]}_spec" }
  watch(%r{^spec/javascripts/(.*)})
end
```

### Specifying Teaspoon Environment

Guard-Teaspoon takes several options, but worth calling out is the environment option. This option allows you to tell Teaspoon where it should look for it's environment file, and is useful if Teaspoon is unable to resolve it's environment.

Guardfile
```ruby
guard :teaspoon, environment: "spec/dummy/spec/teaspoon_env.rb" do
end
```

### Available Options

...document when this is better hammered out...


## License

Licensed under the [MIT License](http://creativecommons.org/licenses/MIT/)

Copyright 2012 [Mode Set](https://github.com/modeset)


## Make Code Not War
![crest](https://secure.gravatar.com/avatar/aa8ea677b07f626479fd280049b0e19f?s=75)

