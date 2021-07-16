# selectize-rails [![Gem Version](https://badge.fury.io/rb/selectize-rails.png)](http://badge.fury.io/rb/selectize-rails)

selectize-rails provides the [selectize.js](https://selectize.github.io/selectize.js/)
plugin as a Rails engine to use it within the asset pipeline.

## Installation

Add this to your Gemfile:

```ruby
gem "selectize-rails"
```

and run `bundle install`.

## Usage

In your `application.js`, include the following:

```js
//= require selectize
```

In your `application.css`, include the following:

```css
 *= require selectize
 *= require selectize.default
```

Or if you like, you could use import instead

```sass
@import 'selectize'
@import 'selectize.bootstrap3'
```

### Themes

To include additional theme's you can replace the `selectize.default` for one of the [theme files](https://github.com/selectize/selectize.js/tree/master/dist/css)


## Examples

See the [demo page](http://selectize.github.io/selectize.js/) for examples how to use the plugin

## Changes

| Version    | Notes                                                       |
| ----------:| ----------------------------------------------------------- |
| hacky-fix  | Hacky fix for comma delimiters on Andoird Chrome            |
|   0.12.5   | Update to v0.12.5 of selectize.js                           |
|   0.12.4.1 | Moved css files to scss to be able to use `@import`         |
|   0.12.4   | Update to v0.12.4 of selectize.js                           |
|   0.12.3   | Update to v0.12.3 of selectize.js                           |
|   0.12.2   | Update to v0.12.2 of selectize.js                           |
|   0.12.1   | Update to v0.12.1 of selectize.js                           |
|   0.12.0   | Update to v0.12.0 of selectize.js                           |
|   0.11.2   | Update to v0.11.2 of selectize.js                           |
|   0.11.0   | Update to v0.11.0 of selectize.js                           |

[older](CHANGELOG.md)


## Hacky Fix for Comma Separation of Tags

### What we have done

1. Fork Selectize JS project https://github.com/selectize/selectize.js into https://github.com/picfair/selectize.js
2. Checkout V2.6, Create a new branch ```ko-delimiter-android-chrome-bugfix```
3. Apply the hacky fix https://github.com/agorodezki/selectize.js/commit/205c3880d24a77844a565fabea23bd0216ce6b77
4. Build selectize ```grunt '--plugins=*'```
5. Fork Selectize Rails gem https://github.com/manuelvanrijn/selectize-rails into https://github.com/picfair/selectize-rails
6. Checkout V2.6, create a new branch ```ko-delimiter-android-chrome-bugfix```
7. Copy the dist files (.js & css) from selectize into the gem (needed to rename some css to scss)
8. Update Gemfile in Rails app to use this version of selectize-rails

### Background

Selectize has a bug on Chome Android: Pressing the comma key does not separate tags.
https://github.com/selectize/selectize.js/issues/321

This is related to Chrome behaviour on Android - it doesn't send proper keyCodes for events
https://bugs.chromium.org/p/chromium/issues/detail?id=118639
(And this is probably because due to Android keyboard behaviour)

Somebody came up with a hacky fix for this bug:
https://github.com/agorodezki/selectize.js/commit/205c3880d24a77844a565fabea23bd0216ce6b77

We want to use the hacky fix, because it's better than the broken version.


## License

* The [selectize.js](http://selectize.github.io/selectize.js/) plugin is licensed under the
[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)
* The [selectize-rails](https://github.com/manuelvanrijn/selectize-rails) project is
 licensed under the [MIT License](http://opensource.org/licenses/mit-license.html)

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
