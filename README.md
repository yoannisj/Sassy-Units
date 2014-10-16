# SassyUnits

Useful Sass functions and mixins to work with CSS units. SassyUnits helps you easily convert, compare and include CSS units in you Sass and Compass files.

CAUTION: The code from this project has not been fully tested yet.

## Installation

SassyUnits is a Compass extension packaged as a gem. The gem has not been published yet, so to install it, you have to follow the steps below.

1. Download the SassyUnits repository from Github as a '.zip' file and unzip it.

2. Open a Terminal window and `cd` to the unzipped repository folder.

3. Build the gem file and install it locally by typing the following commands in your Terminal:

        gem build SassyUnits.gemspec

        gem install SassyUnits-0.1.0.gem

4. Require the extension in you Compass config file.

        require 'SassyUnits'

5. Import the sass files in your project

        @import "SassyUnits";

You are now ready to go ! Just make sure you read the Global section below, you might need to override the globals' default values in order for all functions and mixins to work as expected.

## Globals

* `$su-support-legacy-rem: false`

    Setting for whether to support browser's who don't understand 'rem'. If set to true, all 'rem' mixins will include a 'px' fallback by default.

* `$su-root-font-size: 16px`

    The font-size that is applied to the `<html>` element in your project. This is the default value for the `$root` argument in all functions and mixins described below. It is used to convert numbers from and to the 'rem' unit.

* `$su-base-font-size: $su-root-font-size`

    The font-size that should be used as default font-size context for 'em' related conversions. It is the default value for the `$context` argument in all functions and mixins described below.

Remember that these are all default values. They can be overriden at any time by passing another value to the function or mixin.

    .foo {
        font-size: 14px;
        padding-right: su-px-to-em(10px, 14px);
    }

## Functions available

All `$value` arguments can be passed as a number but also as a list of numbers. If passed a list, the function will be applied to each individual item and return the list of results.

If a value of any other type than 'number' is passed, it will be ignored and returned as is. Additionally, a warning will be thrown in case an error occurs later in the code.

### Utilities

* su-strip-units( $value )

### Unit Conversion

* `su-px-to-em( $value[, $context ])`
* `su-px-to-rem( $value[, $root ])`
* `su-em-to-px( $value[, $context ])`
* `su-em-to-rem( $value[, $context, $root ])`
* `su-rem-to-px( $value[, $root ])`
* `su-rem-to-em( $value[, $context, $root ])`

### Math

All math functions will automatically convert the second term of the calculation to the same unit as the first term. This means you can do something like `su-add(10px, 2em);`.

* `su-add( $term1, $term2[, $context, $root ])`
* `su-subtract( $term1, $term2[, $context, $root ])`
* `su-multiply( $factor1, $factor2[, $context, $root ])`
* `su-divide( $divident, $divider[, $context, $root ])`
* `su-ratio( $term1, $term2[, $context, $root ])`

## Mixins available

* `su-rem($property, $value[, $context, $root, $fallback ])`

    Dynamically includes a given css property and automatically converts its specified value to 'rem'. Optionally adds a 'px' fallback for browsers not supporting the 'rem' unit.