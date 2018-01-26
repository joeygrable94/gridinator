# Gridinator

Welcome to Gridinator, a SASS/SCSS prototyping framework which allows you to write production ready code at a rapid development pace.

View the latest stable version in use at [JoeyGrable.com/git/Gridinator](http://joeygrable.com/git/Gridinator/)

## To Do
- add CSS3 mixins
    - box-shadow
    - transition
    - perspective
    - transitions (2D & 3D)
    - box-shadow
- test case and code refactoring
- add examples to README


## Getting Started

1. clone the repository into your css folder
2. customize settings inside base/config-base.scss
3. add your custom styles to base/build-camp.scss
4. compile the sass into css to build your Gridinator

```
sass gridinator.scss:gridinator.css
```



## Naming Conventions

Gridinator uses the follow rules when naming classes, variables, mixins and functions.



### Classes & SASS Variables

```
.classes-like-this {
    css-property: $var-block-element-modifier;
}

```



### Primed Mixins & Functions


```
@mixin name-property-action(
    $variable-one: $config-default-1,
    $variable-two: $config-default-2
) {
    // do stuff with defaults
}

```



## File Structure & Details

```
Gridinator/
    gridinator.scss    // compiles everything into Gridinator.css
    base/
        build-camp.scss
        config-base.scss
    components/
        typography.scss
        forms.scss
        tables.scss
        buttons.scss
    modules/
        internal.scss
        functions.scss
        mixins.scss
    vendors/
        reset.scss
        normalize.scss
        vendors/animate/animate.scss
        color/
            color-me-sass.scss
            blend-modes.scss
```



### Base

- the base foler is where you will configure your base and build your camp
- these files are essential for simple Gridinator implementations



### Components

- think of Components as the CONTROLLERS that output the CSS styles configured in the base/config-base.scss and base/build-camp.scss files
- components contain foundational styles that are calculated using variables from the config file, and mixins or functions from the modules folder



### Modules

- think of modules as the LOGIC that calculates styles
- modules are mixins or functions that are used internally by Gridinator
- they are used by variables components or in your base/build-camp.scss file



### Vendors (dependencies)

- reset.scss        (recommended)
- normalize.scss    (recommended)
- animate.scss      (as needed)
- colorMeSass       (as needed)
- blendModes.scss   (as needed)



## Order of Implementation

- this is the order in which gridinator compiles and executes

1. Import Vendors
2. Establish Base
3. Import Modules
4. Create Components
5. Build Camp





# Build Your Gridinator

- Gridinator is unique because it is easy to rapidly implement a base wireframe to build your website off of
- Additionally, Gridinator modules are "primed mixins & functions" and is discused in the following section
- the sections below outline how to implement Gridinator quickly, and then how to fully customize the mixins for your use



## Primed Mixins & Functions

- Gridinator mixins are already primed with the default values from your config file
- this means editing primary website styles are as easy as editing the “base/config-base.scss” file then compiling the sass into css
- if you want full customization, it is recomended you establish your web-styles Gridinator in the base/config-base.scss file, then implement your custom mixins on your site specific DOM elements in the base/build-camp.scss file (examples provided below)



### Primed Mixin & Function Usage:


```
.inside-class-or-id {

    // call the mixin or function with config defaults
    @include name-property-action();

    // call but overwrite the defaults to customize
    @include name-property-action(
        $variable-one: overwrite,
        $variable-two: overwrite
    );
}

```



## Configure Base (config-base.scss)

- the configuration file contains everything you need to customize the base styles of your website



###  CSS Grid

```
$gridinator-cols: "repeat(2, 1fr)";
$gridinator-rows: "repeat(2, 1fr)";
$gridinator-gap: 0px 0px;
```



### Responsize Media

```
$breakpoint-sm: 420px;
$breakpoint-md: 760px;
$breakpoint-lg: 1080px;
$breakpoint-xl: 1440px;
```



### Color

```
// palettes
$color-primary:     $bluePrimary !default;
$color-secondary:   $yellowGoldmetal !default;
$color-tertiary:    $redDanger !default;

// states
$color-success:     $greenSuccess !default;
$color-info:        $blueInfo !default;
$color-warning:     $yellowWarning !default;
$color-error:       $orangeDark !default;
```



### Typography

```
// load typography.
$load-typesettings: true !default;

// sets the html and body tags height & width to 100vh/vw & 100%/100%
$full-screen-responsive: true !default;

// The vertical grid unit. Margin, padding, and line-height are set to
// multiples of this value. This is the value that determines the baseline
// for our vertical rhythm. The default value of 6px allows more fine
// tuned designs that still obey vertical rhythm.
$baseline-unit: 8px !default;

// This gives type an ideal line-height. The value that multiplies
// the $baseline-unit to get the $baseline-height.
$baseline-mltp: 4 !default;

// Base font size in pixels, gets converted to ems
$base-font-size: 18px !default;

// Modular scale ratio is used to calculate different font sizes
$ratio-modular-scale: 1.5 !default;

// paragraph-indent option sets paragraphs indent of the first line
// of a new paragraph ON or OFF. Indents all paragraphs execpt
// the first on in a group of p tags (p + p)
$paragraph-indent: true !default;

// paragraph-justify sets paragraphs ragged right or justified.
$paragraph-justify: false !default;

// base font family (paragraph content)
$base-font-family: Cambria, "Hoefler Text", Utopia, "Liberation Serif", "Nimbus Roman No9 L Regular", Times, "Times New Roman", serif !default;

// headers fonts
$base-font-headers: "Helvetica Neue", Helvetica, Arial, "Liberation Sans", FreeSans, sans-serif !default;

// monospaced fonts
$base-font-mono: Consolas, "Andale Mono WT", "Andale Mono", "Lucida Console", "Lucida Sans Typewriter", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Liberation Mono", "Nimbus Mono L", Monaco, "Courier New", Courier, monospace !default;
```



### Elements

```
// borders
$border-width-default: 1px;
$border-style-default: solid;
$border-color-default: $black30;
$border-radius-default: $baseline-mltp;
```



### Forms

```
// label
$form-label-font-weight: 400;

// input
$form-input-color: $black;
$form-input-background-color: $transparent;
$form-input-box-shadow: 0px 0px 5px -2px $color-primary;

// input border
$form-input-border-width: 1px;
$form-input-border-color: $grayLight;
$form-input-border: $form-input-border-width solid $form-input-border-color;
$form-input-border-radius: 0px;

// disabled
$form-input-disabled-color: $black10;

// input focus
$form-input-focus-color: $black;
$form-input-focus-background: $transparent;
$form-input-focus-border-color: $color-primary;
$form-input-focus-box-shadow: 0px 0px 5px -2px $color-primary;
```



### Tables

```
$table-row-bordered: true !default;
$table-row-striped: true !default;
```



### Buttons

```
// base
$btn-font-size: inheret;
$btn-font-weight: 400;
$btn-border-radius: 4px;
$btn-border-width: 2px;
$btn-border-style: solid;
$btn-border-color: $black;
$btn-link-disabled-color: $graySilver;

// default
$btn-default-color: $white;
$btn-default-background: $black;
// border
$btn-default-border-width: $btn-border-width;
$btn-default-border-style: $btn-border-style;
$btn-default-border-color: $black;
    // :hover
    $btn-default-color-hover: $white;
    $btn-default-background-hover: $black70;
    // :hover border
    $btn-default-border-width-hover: $btn-border-width;
    $btn-default-border-style-hover: $btn-border-style;
    $btn-default-border-color-hover: $black;

// additional: primary, secondary, tertiary, info, warning, error
...
```



## Build Camp (build-camp.scss)



### Primed Mixins



