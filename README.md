# Crossass Mem

A module-relative rem unit library (mixin / function) for Sass.

Each HTML/CSS module can be separately scalable with Crossass Mem.

```scss
// Defines the HTML font-size for the base REM value
@include x-config('x.mem.rem-base', 16px);

html {
    font-size: 16px;                        // 1Rem = 16px
}
article {
    // Defines the base MEM value for this module
    @include x-mem-base(.75rem);            // 1Mem = .75Rem (12px)

    font-size: x-mem-base-fallback();       // 12px the fallback below
    font-size: x-mem-base();                // .75Rem = 1Mem (12px)

    h1 {
        font-size: x-mem-fallback(2)        // 24px: the fallback below
        font-size: x-mem(2);                // 1.5Rem = .75Rem * 2Mem (24px)
    }
}
```

## Features

* Module-relative rem value (MEM unit)
* Fallbacks for legacy browsers (such as IE8)
* Multiple and nestable base mem values

## Em, rem problems

Nowaday, em and rem unit are widely used for building scalable Web.
However they have a few problems with the scalability / modularity, especially with the font-sizing.

Unit | Relative to    | Use case |
--- | --- | --- |
em | parent element | [em](http://jsfiddle.net/whizark/GA8hN/)
rem | root (html) | [rem](http://jsfiddle.net/whizark/HT6UD/)
mem | any | [mem](http://jsfiddle.net/whizark/hkR7z/)

The table below is a comparison table about the scalability against each kind of modification.

Unit | Base font-size | Structure | Module font-sizing
--- | --- | --- | --- | ---
em   | [Good](http://jsfiddle.net/whizark/3LPb6/) | **[Poor](http://jsfiddle.net/whizark/8n7g8/)** | [Good](http://jsfiddle.net/whizark/2RHqp/)
rem  | [Good](http://jsfiddle.net/whizark/mSPuD/) | [Good](http://jsfiddle.net/whizark/KcG86/) | **[Poor](http://jsfiddle.net/whizark/7Vhu7/)**
mem  | [Good](http://jsfiddle.net/whizark/rrsME/) | [Good](http://jsfiddle.net/whizark/39dS8/) | [Good](http://jsfiddle.net/whizark/jyBtL/)

With Crossass Mem, you can easily/flexibly handle rem-based sizing.

## Requirement

* [Sass](http://sass-lang.com/) 3.3.0+

## Installation

```sh
bower install crossass-mem
```

or just copy ```crossass-mem``` folder and ```crosass-config``` folder of [Crossass Configuration](https://github.com/whizark/crossass-config) into your project.

## Usage

### Import

```scss
@import 'bower_components/crossass-config/scss/config';
@import 'bower_components/crossass-mem/scss/mem';
```

or

```scss
@import 'your-folder/crossass-config/scss/config';
@import 'your-folder/crossass-mem/scss/mem';
```

### Configuration

```scss
// Defines the HTML font-size for the base REM value
@include x-config('x.mem.rem-base', 16px);

html {
    font-size: 16px;  // This should be the same as `x.mem.rem-base` value
}
```
