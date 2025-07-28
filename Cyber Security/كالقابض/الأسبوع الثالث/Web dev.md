---
share_link: https://share.note.sx/rhp4z66f#J4Lki+Gi4RFSw+OQqELMIzpyaIpGfk7oGoxLh4hSN9o
share_updated: 2025-07-26T23:27:38+03:00
---

## HTML 

`<!DOCTYPE HTML>`: idenitifies the document as HTML5 document.
`<head>`: page information.
`<title>`: page title, the one that appears on browser tab.

`<body>`: page's content.
`<h1>...<h6>`: six sizes of headings.
`<img>`: adds an image.
`<form>`: creates a form that's used to get user's data.
`<input type="">`: input elements are the elements used to get data from users, with `type` attribute you can use different input types.
`<script>`: adds javascript to page.

## CSS
CSS can be used in the head tag or inline(in the same line as the element) using `style` attribute or in a sperate `.css` file.

CSS uses box-model which treats elements as boxes with margin(outer space) and padding(inner space).

Elements are selected through different means `#id`(unique identifier), `.class`(groups properties), `tagname`: e.g `p` or using an attribute `input[type="text"]` : selects all inputs with `type="text"`.

CSS code is written in blocks 

```css
#home {
	color: red;
}
```

CSS uses specificity to determine what rules to apply: inline CSS comes first, then id then class, and lastly tagname

>note: using `!important` overrides this behaviour.


## Javascript

Javascript is a scripting language used to add interactivity to web pages, it can listen and perform browser events(BOM) and manipulate page structure(DOM). 

Javascript is a prototype-based language(everything is a prototype) with C-like syntax.

```js
function hello(name) {
	alert("Hello" + name);
}
```

Javascript is a language with many quirks like `Type Coercion` which allows the compiler(yes Javascript has a compiler) to change data types in different situations.

### let vs var vs const

`const` is a variable that can be never redeclared 

you can't do

```js
const x = 5;
x = 6;
```

it will throw an error, while you can do that in let and var there's a difference between them which is respecting block scope.

As you can't access `let` outside its scope.