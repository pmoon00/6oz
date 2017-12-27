# noname.js

A JavaScript library using intuitive templating and Google's Incremental DOM library to efficiently update data changes to the real browser DOM.

## Getting Started

You will need to download and place both the Incremental DOM and noname.js JavaScript files on your website.  Load Incremental DOM first.  The copy of Incremental DOM in this repository has a bug fix that sets the elements actual properties for attributes like `value`, `checked`, `disabled`, etc.

```
<script type="text/javascript" src="incremental-dom-min.js"></script>
<script type="text/javascript" src="noname.min.js"></script>
```

### Templating

Templating is done using code blocks.  Within the code blocks you can use normal JavaScript.  Simple!  The code blocks are inspired by and match to ASP.Net Web Forms code blocks.  To start a code block write `<%` and to close a code block write `%>`.


#### Rendering Data
To render data in your template that is not HTML encoded use the start block `<%=`.  Use this if you wish to write in HTML into the template.

To render data in your template that is HTML encoded use the start block `<%:`.  Use this if you wish to write in HTML into the template.

For the examples below we are using the following variable
```
var templateData = {
	"htmlText": "<p>Hello world</p>"
};
```
**Template 1**
```
<div><%=htmlText %></div>
```
*will yield*
```
<div><p>Hello world</p></div>
```
**Template 2**
```
<div><%:htmlText %></div>
```
*will yield*
```
<div>&lt;p&gt;Hello world&lt;p&gt;</div>
```

#### JavaScript In Your Template
You can run JavaScript right in your template.  This is useful to conditionally render and/or loop through data in your render logic.

For the example below we are using the following variable
```
var templateData = {
	"header": "My Example",
	"showHeader": true,
	"items": [
		"Hi there",
		"Hello mate",
		"Gidday",
		"Mate",
		"Dave"
	]
};
```
**Template**
```
<% if (showHeader) { %>
<h1><%:header %></h1>
<% } %>
<ul>
<% for (var i = 0, l = items.length; i < l; i++) { %>
	<li><%:items[i] %></li>
<% } %>
</ul>
```
*will yield*
```
<h1>My Example</h1>
<ul>
	<li>Hi there</li>
	<li>Hello mate</li>
	<li>Gidday</li>
	<li>Mate</li>
	<li>Dave</li>
</ul>
```

## Authors

**Phillip Moon**

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details