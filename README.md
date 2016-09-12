# Axiom-Flex-Grid
A versatile SCSS/SASS Flexbox grid system, utilising data attribute selectors for maximum versatility and readability.

## Getting Started
After including the Axiom Grid System in your project, you can include the grid markup using: `@include ag-grid`. Configure the settings using the `$ag` map. Full documentation coming soon.

## FAQ
**Why attribute selectors?**
Despite the bad rep unqualified attribute selectors receive, they're really powerful, and enable us to keep our markup clean and readable. No longer will your grid turn your classname into numerical-acronym soup - just inspect the source of this page and you'll see for yourself.

Attribute selectors also allow us more powerful targeting; We can apply our base styling to the attribute, and then use the attribute value for specifics. This makes it much, much easier to add new modifiers and adjust properties like padding for different breakpoints.

Further Reading: [CSS Performance Revisited](https://benfrain.com/css-performance-revisited-selectors-bloat-expensive-styles/)

**But wait, aren't attribute selectors bad?**
Some people might have you believe so - while they may have an impact on old browsers (and who wants to work with them anyway?), these days they aren't a huge performance concern - your 200kb+ of jQuery plugins is likely a much bigger issue! However, if anyone does find performance issues, please let me know!

**What's with the @ Syntax? This seems wrong!**
The @ syntax is based on [this excellent article from Harry Roberts csswizardry](http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)

**But doesn't using a grid create bloat, what about all those classes I don't use?**
If you're worried about CSS bloat, you should've already heard about [uncss](https://github.com/giakki/uncss).
