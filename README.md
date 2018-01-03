# RegEx Snippets
Useful RegEx snippets that are categorized and searchable (see below)
* **Contributions are welcome**! Please read our CONTRIBUTING, CODE_OF_CONDUCT, and LICENSE files to get started. RegEx snippet ideas are located in IDEAS.md.
* **Errors?** Submit an issue, or even better, submit a PR fixing the issue!
* Code examples use Javascript, but the use of RegEx should not differ significantly across languages.

## Table of Contents

## Snippets

### Files
**Verify whether a string is a image filename**
```
/^.+\.(jpg|jpeg|png|gif|bmp|svg)$/gi.test(str) //Returns either true or false
```

---

### Miscellaneous
**Verify whether a `str` is a valid hexadecimal color**
```
/^#([0-9a-f]{3}$|[0-9a-f]{6}$)/i.test(str) //Returns either true or false
```

**Verify ZIP Codes (5 digit and 9 digit)**
```
/^[0-9]{5}(-[0-9]{4})?$/.test(str) //Returns either true or false
```

---

### Numbers

**Remove dollar signs and comma separators from a number**:
```
str = str.replace(/(\$|\,)/g, ""));
```

**Remove leading zeroes in a number**:    
```
str = str.replace(/^0{2,}/g, "");
```

---

### Web

**Extract URL from an anchor tag**
For example, if `str` = "<a href = 'https://www.google.com'></a>", this RegEx would return "https://www.google.com".  

```
str.match(/<a\s+(?:[^>]*?\s+)?href ?= ?["']([^'^"]*)["'][^>]*>/i)[1] 
```

**Match all content within a specific HTML tag** (*Replace "p" with whatever tag you want*)
```
str.match(/<p>(\n|.)*<\/p>/gi); //Returns either null or an array of matches
```

**Match all HTML tags**
```
str.match(/<\/?.+>/g); //Returns either null or an array of matches
```

