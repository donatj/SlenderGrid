# SlenderGrid

SlenderGrid is **not another CSS Grid Framework**.  Instead, it is a bite-size tool-kit for building **semantic** grid based HTML and CSS.

SlenderGrid takes advantage of modern CSS3. Utilizing `box-sizing: border-box` and percentage widths to make using Grids amazingly simple and clean.

[Click here for a demo](https://cdn.rawgit.com/donatj/SlenderGrid/master/example/example.html) of SlenderGrid in action.

## What is SlenderGrid

SlenderGrid is a remarkably simple [Sass powered](http://sass-lang.com/) grid system. It allows ***you*** to develop semantic responsive grid designs as you see fit.

It contains **none** of the usual inelegant and non-semantic `grid_7` / `container_12` nonsense other frameworks are based on.  There are in fact no predefined classes or ids. 

### Concept

SlenderGrid has two essential entities - boxes and box-containers. In other Grid CSS Framework's these would be pre-defined for you in a non-semantic manner, but in SlenderGrid we define these ourselves using semantic class naming.

Boxes are the main building block. They need you to define their width, which is stated as a fraction using the `box-size` Sass mixin. 

For example, a box taking up two thirds width is declared `@include box-size(2/3);`.

A box-container exists to contain one or more boxes. Box containers are defined using the `box-container` Sass mixin. 

## Example

In this example we have a simple content area and sidebar. `<main>` will be our container for our grid items, we want content to take three quarters of the space, and sidebar to take one quarter.

```html
<main>
	<div class="content">content...</div>
	<div class="sidebar">sidebar</div>
</main>
```

To do this we simply import SlenderGrid into our SCSS or SASS file, mark main as a box-container, and define the sizes for content and sidebar.

```scss
@import "slendergrid";

main {
	@include box-container;
}

.content {
	@include box-size(3/4);
}

.sidebar {
	@include box-size(1/4);
}
```

This can be simply made responsive as follows. 

In the following example when the window or device is smaller than 500px wide, the content switches to a single column.

```scss
@import "slendergrid";

main {
	@include box-container;
}

.content {
	@include box-size(3/4);
	@media screen and (max-width: 500px) {
		@include box-size(1/1);
	}
}

.sidebar {
	@include box-size(1/4);
	@media screen and (max-width: 500px) {
		@include box-size(1/1);
	}
}
```