# Nested Fluid Grid Mixin (LESS)

**tl;dr** Make your grids on the presentation layer for fun and profit.

Most of the grid systems I've found suffer from one limitation: they rely on utility classes in the markup. Utility classes are a great convenience when you have complete control over the markup, but often you don't have that control, and when you do, the implementation is involved.

Sometimes when you want to put one dumb class on one stupid div, you have to write PHP, or write Twig, or do some other thing that's a step or two removed from the simple act of adding a class to an HTML element. Sometimes you have to find a buried config page and enter your class there, only to realize you'll need to find a dozen and a half other config pages and make the same update. When you come back to this project six months later you'll have to remember that the class is applied in some field on some config page in the UI, and NOT in the code were you could just 'Find in project'. And what about changing spans across breakpoints?

But, you know, this is nobody's fault. It's also not your problem anymore.

## Enter the mixin

The Nested Fluid Grid Mixin adapts [my LESS grid dealy](https://github.com/arti5m/nested_fluid_grid) (based on davist11's [nested-responsive-grid](http://davist11.github.io/nested-responsive-grid/)) for use as a convenient LESS mixin to facilitate authoring grids on the presentation layer--where they probably belong.

## Example usage

```LESS
.masthead__inner {
  > div {
    .resp(@desktop, {
      #grid;.row();
      > .col-1 {
        #grid;.span(4);.first-col();
      }
      > .col-2 {
        #grid;.span(8);
      }
    });
  }
}
```