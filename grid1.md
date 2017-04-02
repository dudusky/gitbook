### Things I've Learned About CSS Grid Layout
*by dudusky*
![](https://cdn.tutsplus.com/webdesign/uploads/2013/11/examplecssgrid.png)
- - -
##### CSS grid looks set to land in browsers in  2017.Until then I will need to enable grid for it to work

-----

#### Grid is designed to be used with flexbox,not instead of it
###### A quick way to think about it is:
    *   Flexbox is for one dimensional layout(row or column)
    *   CSS grid is for two dimensional

- - -
***
### THe Downsides to CSS Grids
* Potentially high amount of unused code.
* Restrictions on layout
* Fixed pixel rether than em/rem or percentage based layout.
* Set number of overrall columns.
* Non sematic markup
* Restrictions on nesting

###### Here"s some typical"page layout" HTML:
```
<body>
  <header class="site-header"></header>
  <main class="main-content"></main>
  <aside class="sidebar"></aside>
  <footer class="site-footer"></footer>
</body>
```
All those major element are direct child of `<body>`,so`<body>` can be the grid and the four major elements are laid out on that grid.

#### Browser Support
==Chrome: none
Safari: none
Firefox: none
Opera: none
IE: 10+
Android: none
IOS: none==

#### Chrome:
==chrome://flags/#enable-experimental-web-platformfeatures==.


![](https://cms-assets.tutsplus.com/uploads/users/30/posts/27238/image/flag.png)


#### Terminilogy

- - -


![](https://cms-assets.tutsplus.com/uploads/users/30/posts/27238/image/grid-terms-lines-rows-columns-cells-.svg)
1. grid lines
2. columns
3. rows
4. cells
- - -
![](https://cms-assets.tutsplus.com/uploads/users/30/posts/27238/image/grid-terms-gutters.svg)
1. gutter

- - -

![](https://cms-assets.tutsplus.com/uploads/users/30/posts/27238/image/grid-terms-area.svg)
1. grid area

#### Grid Rules
* Firstly we need to declare that our container element is a grid using a new value for the `display` property:
```css 
     .container {
     display: grid;
     }
```

#### Conclusion
1. Create a conteiner element, and declare it`display: grid`.
2. use that sae container to define the grid track using the `grid-template-colums`and `grid-template-rows`properties.
3. place child elements within the container.
4. Specify where ech child belongs on the grid by declaring its `grid-clumn`and `grid-row`.
5. Grid will accept flexible units in combination with fixed units of measurnments.
6. We needn't declare gutters within our `grid-templeta`,we can use the `grid-gap` properties instead.
7. `grid-gap` means we are less bound to positioning our grid items-we can hand more responsibiluty overto auto-placement.


# Flexible Units

### Relative lengths
| unit | relative |
|--------|--------|
|em|font size of the element     |
|ex|x-height of the element"s font|
|ch|width of the "0" glyph in the element's font|
|rem|if (body{font-size:16px}){1rem = 16px}|
|vw|if(window.width=960px){1vm = 9.6px}|
|vw|if(window.height=1000px){1vh = 10px}|
|vmin|vmin = window.heigh<window.width?window.height&&window.width|
|vmax|vmin = window.heigh>window.width?window.height&&window.width|
|fr|Used to distribute ramaining space in a flex layout computaion|

### Absolute lengths:
|unit|definition|
|----|----|
|cm|centimeters|
|mm|millimeters|
|in|inches;1inis equal to 2.54cm|
|px|pixels; 1px = |
|pt|points; 1pt = |
|pc| picas; 1pc = 12pt|


##### em
```css
	body {
		font-size: 14px;
	}
    div {
    font-size: 1.2px /*calculated at 14px*1.2=16.8px*/
    }
```



```html
<body><!--font-size: 14px-->
    <div>
        Test <!-- 14 * 1.2 = 16.8px -->
        <div>
            Test <!-- 16.8 * 1.2 = 20.16px -->
            <div>
                Test <!-- 20.16 * 1.2 = 24.192px -->
            </div>
        </div>
    </div>
</body>
```

##### rem stands for "root"
```css
     .container {
        width: 70rem; /*70*14=980px*/
     }
```

##### vh and vw

Responsive web design techniques rely heavily on percentage rules.However,CSS percentage isn"t always the best solution for every problem. CSS width is relative to the nesrest containing parent element. What if you want to use the width of height of the viewport instead id the width of the parent elememt?
```css
   div {
     width:100vh /*1/100 of the height of the viewport*/
   }
```
* For example,if the browser"s height is `900px`, `1vh`would evaluate to 9px;
* If the viewport width is 750px,1hwwould evaluate to 7.5px;

##### vmin and vmax

`vh`and `vw`are always relate to the viewport height and width,respectively,`vmin`and`vmax`are relared to the maximum or munimum of those widths and heights, dependig on which is smaller and larger.
* for example,if the browser was set to 1100px wide and the 700px tall,`1vmin`would be 7px and `1vmax` would be 11px.

### Calculation:`calc()`,`min()`,`max()`
* Those function can be used wherever `length`,`frequenct`,`angle`,`time`,`number`values.

## Redefining Grid Areas with Media Queries
