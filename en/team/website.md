# Ruls for making website

---

## Form

### Mobile Phone number

Make sure you know the countries which are allowed in the field. If more than one country is allowed, make sure use dropdown to select country code.   
When saving to database, save the full, formated number, in STRING format

> +61 444 444 444  
> +86 158 0000 0000

---

## Referencing scripts & files

### The protocol-relative URL

Most often, file loading from external URLs should be avoided as it increases website reponse time. Consider compiling the file using automation gools such as [GulpJS](//gulpjs.com), [GruntJS](//gruntjs.com/) or using module bundling tool such as [Webpack](//webpack.github.io/).  
If it is absolutely necessary to include external URLs, it is recommended to link the file using [Protocol-relative URL](https://en.wikipedia.org/wiki/Wikipedia:Protocol-relative_URL), E.g.

```
<script type = 'text/javascript' src="//path/to/your/script/script.js">
<link rel="stylesheet" href="//path/to/your/css/script.css">

##Links
```

---

## Linking

### Internal Links

Just reference internal links as following

```
<a href="/path">
```

### External Links

When referencing external links, make sure to include **target="\_blank"** in the anchor tag, so that after user clicked open the external link in the new tab, the current link still exists as a seperate tab/window, and user keep track of our current website and can always come back to this tab.

```
<a href="/path" target="_blank">
```



