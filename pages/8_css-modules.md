# CSS Modules

<!-- Let's round out our evaluations by taking a look at CSS-modules -->

---

#### CSS Modules

- CSS-like syntax
- Build time CSS-in-JS

<!--
Written like normal CSS but is actually build time CSS in JS.
The advantage of this is that it can be imported as a module into your components and it uses a build step to scope your styles specifically to that component -->

---

#### CSS Modules

```css
/* Heading.module.scss */
.root {
	background: "navy";
	color: "plum";
	padding: 1rem;
}
```

<!--
Fist we'll define our styles in a .module.scss file.
Looks and feels just like we're writing plain 'ol CSS.
-->

---

#### CSS Modules

```jsx {all|2|5}
// Heading.tsx
import styles from './Heading.module.css'

export const Heading = ({ children }) => (
	<div className={ styles.root }>
		<h1>{ className }</h1>
	</div>
)
```

<!-- Then we'll go over to our Heading component

click

and import the styles we defined in our .module.scss file as a JavaScript module.

click

Then we'll apply our root class we defined by keying the root off of the styles module we imported -->

---

#### CSS Modules

```css
.Heading-root-cnq0T {
	background: "navy";
	color: "plum";
	padding: 1rem;
}
```

<!-- Then, when we look at the CSS in the browser we'll see something looks like this. First, you'll notice that it's hashed, so we know it's scoped to the element that was explicitly assigned this class.

However, unlike with runtime CSS-in-JS, this CSS is actually built with the application and sent to the browser as a static CSS file. -->

---
layout: two-cols
---

#### CSS Modules

# 👍

::right::

 - Locally scoped
 - Explicit dependencies
 - Familiar syntax

<!-- 
pros
- Locally-scoped
    - Hash helps ensure they are locally scoped
- Explicit dependencies
    - Stylesheets need to be imported into the components they are used all our styles have explicit dependencies
    - This also means we have an import map so styles that aren't used can be tree-shaken
- looks and feels like regular CSS
-->

---
layout: two-cols
---

#### CSS Modules

# 👎

::right::

 - DevX
 - Runtime theming
 - Typesafety

<!--

cons
- DevX - No great path forward to use props & state for styling in a way that’s reusable
  - often end up rolling our own globally-scoped atomic CSS
- Doesn't readily support Runtime theming: Even scss compiles down to the underlying values
  - have to create my own css variable layer in my sass token layer
- no type safety
-->