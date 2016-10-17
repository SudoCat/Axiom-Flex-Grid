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
The @ syntax is based on [this excellent article from Harry Roberts csswizardry](http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)

**But doesn't using a grid create bloat, what about all those classes I don't use?**  
If you're worried about CSS bloat, you should've already heard about [uncss](https://github.com/giakki/uncss).

**What about IE Support?**
We have now added IE support for 10 and 11 - older versions will probably require some further work. You can toggle IE support with the ie-support setting.

## Configuration
The settings can be configured using the `$ag` map variable. The configuration format is as follows:

```scss
$ag: (
  max-width: 1680px,
  columns: 12,
  gutters: 3em,
  include-fiths: true,
  include-alignment: true,
  reduce-fractions: true,
  responsive: (
    mobile: (4, 6, 8, 12),
    tablet: (3, 4, 6, 8, 9, 12),
    touch: (3, 4, 6, 8, 9, 12),
  ),
  breakpoints: (
    mobile: max-width 640px,
    tablet: 640px 1280px,
    touch: max-width 1280px,
  ),
  ie-support: true
);
```

## Demos
[Codepen](http://codepen.io/SudoCat/full/wzBzoG/)

## Todo
- Add settings for responsive cell padding
- Write documentation
- Crossbrowser testing
- Add automated testing suite
- Provide option to use fully qualified selectors