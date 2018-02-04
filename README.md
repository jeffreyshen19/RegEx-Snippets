# RegEx Snippets
Useful RegEx snippets that are categorized and searchable (see below)
* **Contributions are welcome**! Please read our CONTRIBUTING, CODE_OF_CONDUCT, and LICENSE files to get started. RegEx snippet ideas are located in IDEAS.md.
* **Errors?** Submit an issue, or even better, submit a PR fixing the issue!
* RegEx snippets are either user-created, or picked from across the web.

## Table of Contents

* [Dates](#dates)
  * Match mm/dd/yyyy
  * Match mon/dd/yyyy
  * Match month names
* [Files](#files)
  * Match image filenames
* [Miscellaneous](#miscellaneous)
  * Match city, state abbreviation
  * Match credit cards
  * Match email addresses
  * Match US Phone Numbers
  * Match valid hexadecimal colors
  * Match social security number
  * Match ZIP Codes (5 digit and 9 digit)
* [Numbers](#numbers)
  * Match dollar signs and comma separators in a number
  * Matching leading zeroes
* [Strings](#strings)
  * Match new lines
  * Match strong passwords (At least one lower case, one upper case, one number, one special character, and 10 characters long)
  * Match usernames (alphanumeric string of a certain length)
* [Web](#web)
  * Extract URL from an anchor tag
  * Match all content within a specific HTML tag
  * Match all HTML tags
  * Match IPv4 Addresses
  * Match Twitter usernames
  * Match URLs
  * Match URL safe strings
  * Match URL slugs

## Snippets

### Dates <a name="dates"></a>
**Match mm/dd/yyyy**  
Accepts mm/dd/yyyy, mm-dd-yyyy, or mm.dd.yyyy and doesn't care about leading zeroes.
```
/^[0-3]?[0-9](\/|\.|-)[0-3]?[0-9](\/|\.|-)[1-9]\d{3}$/gi
```

**Match mon/dd/yyyy**  
Accepts mon/dd/yyyy, mon-dd-yyyy, or mon.dd.yyyy and doesn't care about leading zeroes or case. For example, will match "jan/10/2017"
```
/^(jan|feb|mar|apr|may|jun|jul|aug|sept?|oct|nov|dec)(\/|\.|-)[0-3]?[0-9](\/|\.|-)[1-9]\d{3}$/gi
```

**Match month names**  
Accepts month names (both full and abbreviated), and doesn't care about case. For example, it will match "January" and "jan".
```
/^(jan(uary)?|feb(ruary)?|(mar)?ch|(apr)?il|may|(jun)?e|(jul)?y|(aug)?ust|sep(tember)?|sept|(oct)?ober|(nov)?ember|(dec)?ember)$/i;
```


---

### Files <a name="files"></a>
**Match image filenames**
```
/^.+\.(jpg|jpeg|png|gif|bmp|svg)$/gi
```

---

### Miscellaneous <a name="miscellaneous"></a>
**Match city, state abbreviation** (Matches "Los Angeles, CA" for example)
```
/[a-zA-Z\s]*, [A-Z][A-Z]/
```

**Match credit cards** (Make sure to strip the string of all commas, spaces, etc. before matching)  
Amex:
```
/^3[47][0-9]{13}$/
```

Discover:
```
/^65[4-9][0-9]{13}|64[4-9][0-9]{13}|6011[0-9]{12}|(622(?:12[6-9]|1[3-9][0-9]|[2-8][0-9][0-9]|9[01][0-9]|92[0-5])[0-9]{10})$/
```

Mastercard:
```
/^5[1-5][0-9]{14}$/
```

Visa:
```
/^4[0-9]{12}(?:[0-9]{3})?$/
```

Visa Mastercard:
```
/^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14})$/
```

**Match email addresses**
```
/^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/i
```

**Match US Phone Numbers**  
Matches ###-###-####, (###) ###-####, and ### ### ####
```
/^(\+\d{1,2}\s)?\(?\d{3}\)?[\s.-]\d{3}[\s.-]\d{4}$/
```

**Match valid hexadecimal colors**
```
/^#([0-9a-f]{3}$|[0-9a-f]{6}$)/i
```

**Match social security number**  
Matches ###-##-####
```
/^[0-9]\{3\}-[0-9]\{2\}-[0-9]\{4\}$/
```

**Match ZIP Codes (5 digit and 9 digit)**
```
/^[0-9]{5}(-[0-9]{4})?$/
```

---

### Numbers <a name="numbers"></a>

**Match dollar signs and comma separators in a number**:
This can be used to strip a number string into an actual number.
```
/(\$|\,)/g
```

**Matching leading zeroes**:    
```
/^0{2,}/g
```

---

### Strings <a name="strings"></a>

**Match new lines**
```
/[\r\n]|$/g
```

**Match strong passwords (At least one lower case, one upper case, one number, one special character, and 10 characters long)**:
```
/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[$@$!%*?&_])[A-Za-z\d$@$!%*?&_]{10,}$/
```

**Match usernames (alphanumeric string of a certain length)**:  
Replace MIN_CHARS and MAX_CHARS with the minimum and maximum length of the username, respectively.
```
/^[a-z0-9]{MIN_CHARS,MAX_CHARS}$/i
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
/<p>(\n|.)*<\/p>/gi
```

**Match HTML tags**
```
/<\/?[^>]+>/g
```

**Match IPv4 Addresses**
```
/^((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/
```

**Match Twitter Usernames**
```
/^@?(\w){1,15}$/
```

**Match URLs**
```
/((([A-Za-z]{3,9}:(?:\/\/)?)(?:[\-;:&=\+\$,\w]+@)?[A-Za-z0-9\.\-]+|(?:www\.|[\-;:&=\+\$,\w]+@)[A-Za-z0-9\.\-]+)((?:\/[\+~%\/\.\w\-_]*)?\??(?:[\-\+=&;%@\.\w_]*)#?(?:[\.\!\/\\\w]*))?)/
```

**Match URL safe strings**
```
/^[a-zA-Z0-9_-]*$/
```

**Match URL Slug**
```
/^[a-z0-9-_]+$/i
```
