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
