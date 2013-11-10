# Compass::Fontcustom

[![Build Status](https://travis-ci.org/glaszig/compass-fontcustom.png?branch=master)](https://travis-ci.org/glaszig/compass-fontcustom)
[![Gem Version](https://badge.fury.io/rb/compass-fontcustom.png)](http://badge.fury.io/rb/compass-fontcustom)
[![Test Coverage](https://coveralls.io/repos/glaszig/compass-fontcustom/badge.png?branch=master)](https://coveralls.io/r/glaszig/compass-fontcustom)
[![endorse](https://api.coderwall.com/glaszig/endorsecount.png)](https://coderwall.com/glaszig)

This is my attempt of integrating [Font Custom](http://fontcustom.com) with [Compass](http://compass-style.org).

## Requirements

Made for ruby 1.9+. Tested on 1.9.3 and 2.0.0.  
You'll need to have fontforge and the [WOFF font toolset](http://people.mozilla.com/~jkew/woff) installed as outlined in the Font Custom [installation instructions](http://fontcustom.com/#installation).

## Installation

Add this line to your application's Gemfile:

    gem 'compass-fontcustom'

or:

    gem 'compass-fontcustom', :github => 'glaszig/compass-fontcustom'

And then execute:

    $ bundle

## Usage

Syntactically it works like Compass' sprites feature.  
You can let Font Custom generate your fonts upon Compass' css compilation:

```css
@import "myfont/*.svg";
@include all-myfont-glyphs;
```

This will setup a proper `@font-face` and generate icon classes named `.icon-<font_name>-<glyph_name>` for each glyph.

### Custom class names

You can also use custom class names using the `<font_name>-glyph()` mixin:

```css
.custom-class-name {
  @include myfont-glyph(glyph-file-name);
}
```

which will result into CSS along the lines of:

```css
.myfont-font, .custom-class-name {
  font-family: "myfont";
}
.custom-class-name:before {
  content: "\f100";
}
```

## Configuration options

### Filename hashing

You can choose to disable file name hashes if you're already using an asset pipeline which handles this for you:
Use the `fontcustom_hash` option in `config.rb`

```ruby
compass_config do |config|
  config.fontcustom_hash = false
end
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License

[MIT](https://raw.github.com/glaszig/compass-fontcustom/master/LICENSE)

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/233dd6a31787ce3672d5e92e97a76965 "githalytics.com")](http://githalytics.com/glaszig/compass-fontcustom)
