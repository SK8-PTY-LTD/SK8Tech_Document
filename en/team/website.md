# Code of Conduct

In this document, we list out our code of conduct.

1. [Elegancy](#elegancy)
1. [Security](#security)

---

# Coding Standard

## Website

### Form

#### Mobile Phone number

Make sure you know the countries which are allowed in the field. If more than one country is allowed, make sure use dropdown to select country code.
When saving to database, save the full, formated number, in STRING format

> +61 444 444 444
> +86 158 0000 0000

### Referencing scripts & files

#### The protocol-relative URL

> Most often, file loading from external URLs should be avoided as it increases website reponse time. Consider compiling the file using automation gools such as [GulpJS](//gulpjs.com), [GruntJS](//gruntjs.com/) or using module bundling tool such as [Webpack](//webpack.github.io/).

If it is absolutely necessary to include external URLs, it is recommended to link the file using [Protocol-relative URL](https://en.wikipedia.org/wiki/Wikipedia:Protocol-relative_URL). 

The following is a good example.

```HTML
<script type='text/javascript' src="//path/to/your/script/script.js">
<link rel="stylesheet" href="//path/to/your/css/script.css">
```

---

## Linking

### Internal Links

Just reference internal links as following

```HTML
<a href="/path">
```

### External Links

When referencing external links, make sure to include **target="\_blank"** in the anchor tag, so that after user clicked open the external link in the new tab, the current link still exists as a seperate tab/window, and user keep track of our current website and can always come back to this tab.

```HTML
<a href="/path" target="_blank">
```

---

# Security

We spend a lot of energy on ensuring and enforcing the security of our apps and websites. 

## Version Control

No code, not a single line of code, should be written without a version control tool. At SK8Tech, we use Github as our default version control tool.

## BackUp

1. For WordPress websites, back up the following files with following frequency
    
    |File|Frequency|Copies|Location|
    |---|---|---|---|
    |Files|Weekly|52|Remote|
    |Database|Daily|365|Remote|

## Virus Scan

1. For WordPress websites, use [Wordfence](https://www.wordfence.com/) to scan virus