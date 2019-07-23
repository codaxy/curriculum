# CSS conventions

Example of a component

```html
<header class="flex-row align-center">
  <ul class="navbar">
    <li class="primary navbar_item active">Home</li>
    <li class="navbar_item">Products</li>
    <li class="navbar_item disabled">Resources</li>
  </ul>
</header>
```


### Block/element name does not contain dashes

YES:
```css
.navbar {
  
}
```

```css
.navbar_menuitem {
  
}
```

NO:
```css
.nav-bar {
  
}

.navbar-menu-item {
  
}

.navbar_menu-item {
  
}

.navbar-menu_item {
  
}

.navbar_menu_item {
  
}
```


### The name of the element class should contain the name of the block class and an underscore (_) 

YES:
```css
.navbar_menuitem {
  
}
```
NO:
```css
.menuitem {
  
}

.navbarmenuitem {
  
}
```

### We don't use prefixes for block, element, state or mod classes

YES:
```
.navbar.selected {
  
}
```

NO:
```
.b-navbar.s-selected {
  
}
```

### Mod and state classes need to be combined with a block/element class in the CSS

YES:
```css
.tab.selected {
  
}
```

NO:
```css
.selected {
  
}
```

### Using child selector (>) when styling elements for a mod or a state is preferred over using descendant selector

YES:
```css
.section.card > .section-body {
  
}
```

NO:
```css
.section.card .section-body {
  
}
```

### Mods are specified before the block/element class. Helpers and state classes are specified after the block/element class.

YES:
```css
.primary.btn {
  
}

.btn.pressed {
  
}
```

```html
<button class="primary btn">Click Me</button>
<button class="btn pressed">Click Me</button>
<button class="primary btn pressed">Click Me</button>
<button class="btn pad-xl pressed">Click Me</button>
```

NO: 
```css
.btn.primary {
  
}
```

```html
<button class="btn primary">Click Me</button>
<button class="pressed btn">Click Me</button>
<button class="btn primary pressed">Click Me</button>
<button class="btn pressed pad-xl">Click Me</button>
```

### Mod for an element needs to specify all states

```css
.btn.selected {
  background: yellow;
}

.primary.btn {
  background: red; // overrides selected state
}

.primary.btn.selected {
  background: lightred;
}
```

### Global utility classes need to contain a prefix describing their function and a dash separator

YES:
```css
.flex-row {
  
}

.size-l {

}
```

NO:
```css
.row {
  
}

.large {

}
```
