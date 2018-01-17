# RegEx Snippets
Useful RegEx snippets that are categorized and searchable (see below)
* **Contributions are welcome**! Please read our CONTRIBUTING, CODE_OF_CONDUCT, and LICENSE files to get started. RegEx snippet ideas are located in IDEAS.md.
* **Errors?** Submit an issue, or even better, submit a PR fixing the issue!
* Code examples use Javascript, but the use of RegEx should not differ significantly across languages.
* RegEx snippets are either user-created, or picked from across the web.

## Table of Contents

* [Dates](#dates)
  * Verify mm/dd/yyyy
  * Verify mon/dd/yyyy
* [Files](#files)
  * Verify whether a string is a image filename
* [Miscellaneous](#miscellaneous)
  * Verify credit cards
  * Verify email addresses
  * Verify US Phone Numbers
  * Verify whether a `str` is a valid hexadecimal color
  * Verify ZIP Codes (5 digit and 9 digit)
* [Numbers](#numbers)
  * Remove dollar signs and comma separators from a number
  * Remove leading zeroes in a number
* [Web](#web)
  * Extract URL from an anchor tag
  * Match all content within a specific HTML tag
  * Match all HTML tags
  * Match IPv4 Addresses
  * Match URLs

## Snippets

### Dates <a name="dates"></a>
**Verify mm/dd/yyyy**  
Accepts mm/dd/yyyy, mm-dd-yyyy, or mm.dd.yyyy and doesn't care about leading zeroes. 
```
/^[0-3]?[0-9](\/|\.|-)[0-3]?[0-9](\/|\.|-)[1-9]\d{3}$/gi.test(str) //Returns either true or false
```

**Verify mon/dd/yyyy**  
Accepts mon/dd/yyyy, mon-dd-yyyy, or mon.dd.yyyy and doesn't care about leading zeroes or case. For example, will match "jan/10/2017"
```
/^(jan|feb|mar|apr|may|jun|jul|aug|sept?|oct|nov|dec)(\/|\.|-)[0-3]?[0-9](\/|\.|-)[1-9]\d{3}$/gi.test(str) //Returns either true or false
```

---

### Files <a name="files"></a>
**Verify whether a string is a image filename**
```
/^.+\.(jpg|jpeg|png|gif|bmp|svg)$/gi.test(str) //Returns either true or false
```

---

### Miscellaneous <a name="miscellaneous"></a>
**Verify credit cards** (Make sure to strip the string of all commas, spaces, etc. before matching)  
Amex: 
```
/^3[47][0-9]{13}$/.test(str);
```

Discover: 
```
/^65[4-9][0-9]{13}|64[4-9][0-9]{13}|6011[0-9]{12}|(622(?:12[6-9]|1[3-9][0-9]|[2-8][0-9][0-9]|9[01][0-9]|92[0-5])[0-9]{10})$/.test(str);
```

Mastercard: 
```
/^5[1-5][0-9]{14}$/.test(str);
```

Visa: 
```
/^4[0-9]{12}(?:[0-9]{3})?$/.test(str);
```

Visa Mastercard: 
```
/^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14})$/.test(str);
```

**Verify email addresses**
```
/^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/i.test(email); //Returns either true or false
```

**Verify US Phone Numbers**  
Matches ###-###-####, (###) ###-####, and ### ### ####
```
/^(\+\d{1,2}\s)?\(?\d{3}\)?[\s.-]\d{3}[\s.-]\d{4}$/.test(phone_num); //Returns either true or false
```

**Verify whether a `str` is a valid hexadecimal color**
```
/^#([0-9a-f]{3}$|[0-9a-f]{6}$)/i.test(str) //Returns either true or false
```

**Verify ZIP Codes (5 digit and 9 digit)**
```
/^[0-9]{5}(-[0-9]{4})?$/.test(str) //Returns either true or false
```

---

### Numbers <a name="numbers"></a>

**Remove dollar signs and comma separators from a number**:
```
str = str.replace(/(\$|\,)/g, ""));
```

**Remove leading zeroes in a number**:    
```
str = str.replace(/^0{2,}/g, "");
```

---

### Web <a name="web"></a>

**Extract URL from an anchor tag**  
For example, if `str` = "&lt;a href = 'https://www.google.com' &gt;&lt;/a&gt;", this RegEx would return "https://www.google.com".  

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

**Match IPv4 Addresses**
```
/^((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/.test(str);
```

**Match URLs**
```
/((([A-Za-z]{3,9}:(?:\/\/)?)(?:[\-;:&=\+\$,\w]+@)?[A-Za-z0-9\.\-]+|(?:www\.|[\-;:&=\+\$,\w]+@)[A-Za-z0-9\.\-]+)((?:\/[\+~%\/\.\w\-_]*)?\??(?:[\-\+=&;%@\.\w_]*)#?(?:[\.\!\/\\\w]*))?)/.test(str);
```
