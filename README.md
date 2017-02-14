# Axiom-Flex-Grid
A versatile SCSS/SASS Flexbox grid system, utilising data attribute selectors for maximum versatility and readability.

## Getting Started
After including the Axiom Grid System in your project, you can include the grid markup using: `@include ag-grid`. Configure the settings using the `$ag` map. Full documentation coming soon.

## FAQ
**Why attribute selectors?**  
Despite the bad rep unqualified attribute selectors receive, they're really powerful, and enable us to keep our markup clean and readable. No longer will your grid turn your classname into numerical-acronym soup - just inspect the source of our demos and see for yourself.

Attribute selectors also allow us more powerful targeting; We can apply our base styling to the attribute, and then use the attribute value for specifics. This makes it much, much easier to add new modifiers and adjust properties like padding for different breakpoints.

Further Reading: [CSS Performance Revisited](https://benfrain.com/css-performance-revisited-selectors-bloat-expensive-styles/)

**But wait, aren't attribute selectors bad?**  
Some people might have you believe so - while they may have an impact on old browsers (and who wants to work with them anyway?), these days they aren't a huge performance concern - your 200kb+ of jQuery plugins is likely a much bigger issue! However, if anyone does find performance issues, please let me know!

**What's with the @ Syntax? This seems wrong!**  
The @ syntax is based on [this excellent article from Harry Roberts csswizardry](http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/). It should ensure that your selectors as easy to read and decipher at a glance.

**But doesn't using a grid create bloat, what about all those classes I don't use?**  
I've tried to make sure that you have plenty of control over what CSS is generated, however if you're still worried about CSS bloat, I recommend checking out the ever-wonderful  [uncss](https://github.com/giakki/uncss).

**What about IE Support?**
I have now added IE support for 10 and 11 - older versions will probably require some further work. You can toggle IE support with the `ie-support` setting, explained in further detail below.

## Configuration
The settings can be configured using the `$ag` map variable. The configuration format is as follows:

```scss
// default Settings
$ag: (
  max-width: 1680px,
  columns: 12,
  gutters: 1em,
  include-alignment: true,
  reduce-fractions: true,
  responsive: (
    '*': (
      breakpoint: null,
      columns: (3, 4, 6, 8, 9, 12)
    ),
    tablet: (
      breakpoint: 768px,
      columns: (3, 4, 5, 6, 7, 8, 9, 12),
      gutters: 2em
    ),
    desktop: (
      breakpoint: 1140px,
      columns: '*',
      gutters: 2em
    ),
    desktopHD: (
      breakpoint: 1440px,
      columns: '*',
      gutters: 4em
    )
  ),
  ie-support: false
);
```

### Max Width
`max-width` defines the maximum size of the grid container. This accepts any unit based value. Defaults to `1680px`.

### Columns
`columns` defines the total number of columns the grid should be divided into. Accepts a number. Defaults to `12`.

### Gutters
`gutters` defines the width of the space between cells. This is the default size which will be used if none are set within the responsive settings. Accepts any unit based value. Defaults to `1em`.

### Include Alignment
`include-alignment` is used to control the output of flexbox alignment attribute selectors. These can be used to very easily adjust the alignment and justification of your grid containers. Accepts boolean values. Defaults to `true`.

If set to true, the following attribute selectors will be generated for you.

```css
[data-grid*=nowrap] {
  flex-wrap: nowrap; }

[data-grid*=dir-column] {
  flex-direction: column; }

[data-grid*=dir-row] {
  flex-direction: row; }

[data-grid*=align-center] {
  align-items: center; }

[data-grid*=align-start] {
  align-items: flex-start; }

[data-grid*=align-end] {
  align-items: flex-end; }

[data-grid*=justify-center] {
  justify-content: center; }

[data-grid*=justify-start] {
  justify-content: flex-start; }

[data-grid*=justify-end] {
  justify-content: flex-end; }

[data-grid*=justify-between] {
  justify-content: space-between; }

[data-grid*=justify-around] {
  justify-content: space-around; }
```

### Reduce/Simplify Fractions
`reduce-fractions` defines whether or not the grid should output the attribute selectors using simplified fractions (`1/2` for one half), or traditional unsimplified fractions (`1/6` for one half). Accepts boolean values. Defaults to `true`.

### Responsive Settings
The `responsive` option is a map of containing the different responsive settings, where the key is the name of the size, and the value is a map containing the settings for that size. The key must be a string. For the default sizes, please set the key to `*`. The map for the size settings must have the breakpoint and columns keys, gutters are optional. If no gutters are set, then the default gutter sizing will be used for that breakpoint.

`breakpoint` must be either a CSS unit value, or null. This value will be passed to `breakpoint-sass`, so you can express a variety of different media queries such as `max-width 768px` for desktop first, or `768px 1140px` to create min/max ranges.

`columns` must be either a list of numbers, defining which columns are to be included within this breakpoint, or a string with the value `'*'`. This allows you to be more selective with which columns are generated for larger/smaller devices, as you often won't need a 1/12 column on smaller sizes. If you simply wish to include all the possible sizes in your breakpoint, you may set this value to `'*'`.

`gutters` must be a CSS Unit value. If you do not wish to change the gutters for this size, please exclude this value.

#### Example
The configuration below would define 3 different sizes: default, tablet and desktop. Let's take a look at what each of those does:
- The default (or mobile) size would include only columns of quarters, thirds, and halves. The selectors for this would have no suffix, due to the `'*'` key.
- The tablet settings would then define cells only available on screen sizes above 768px in width, with 2em gutters, all sizes except 1/12 and 11/12 and use the suffix `tablet`, as defined by the key.
- The desktop settings would define cells available only on screen sizes above 1280px, also with a 2em gutter, but including all possible cell sizes.
Hopefully, this should enable you to create pretty much whatever grid your project might need.

```scss
...
responsive: (
  '*': (
    breakpoint: null,
    columns: (3, 4, 6, 8, 9, 12)
  ),
  tablet: (
    breakpoint: 768px,
    columns: (2, 3, 4, 5, 6, 7, 8, 9, 12),
    gutters: 2em
  ),
  desktop: (
    breakpoint: 1280px,
    columns: '*',
    gutters: 2em
  )
),
...
```

### IE Support
If you wish to enable IE support, please set the `ie-support` setting to true. Please be aware that this will add max-widths onto all of your grid cells to maintain correct sizing in internet explorer. Accepts a boolean value. Defaults to true.

## Demos
[Codepen](http://codepen.io/SudoCat/full/wzBzoG)

## Todo
- Expand documentation
- Crossbrowser testing
- Provide option to use fully qualified selectors
- Add example test cases
- Add automated testing suite

## Potential Feature Ideas
- Allow configuration of different column layouts for different devices
