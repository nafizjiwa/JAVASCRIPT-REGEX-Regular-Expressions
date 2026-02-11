# 
# **🔥Summary **REGEX ONE‑PAGE REGEX TOKENS AND FLAGS CHEAT SHEET**

## **1. Character Classes (these MATCH characters)**
- Tokens appear *inside* the pattern and control matching behavior.
- character class is defined by [...];

| Token | Name | Meaning |
|-------|--------|---------|
| `.` | Wildcard | Match any ONE character except newline |
| `\w` | Word Character Class| Match any ONE word character (A–Z, a–z, 0–9, `_`) |
| `\W` | Match ANY character NOT a word character |space, punc, sym, emoj...|
| `\d` | Digit Character Class| Match any ONE digit (0–9) |
| `\D` | Digit Character Class| Match any ONE character that is NOT a digit |
| `\s` | Whitespace Character Class | Match any ONE whitespace character space, tab, newline 
| `\S` | Whitespace Character Class |Match any ONE character that is NOT whitespace |
|[...]| Character Class | Means Match exactly 1 Character between the brackets|
| `[abc]` | Character Class| Match ONE of: a, b, or c or of listed|
| /[abc]{3}/ | Character Class |match exactly 3 characters from the set |
|/[abc]+/| Character Class|Match one or more characters, each of which must be a, b, or c.|
|/[abc]*/| Character Class|Match zero or more characters, each of which must be a,b,c even ''|
| `[^abc]` | Negated Character Class| Match ONE character that is NOT a, b, or c or NOT in list|
| `[a-z]` | **Literal Pattern**| Match ONE lowercase letter a–z |
| `[A-Z]` | **Literal Pattern**| Match ONE uppercase letter A–Z |
| `/abc/` | **Literal Pattern** | Match the exact text “abc” |
| `/abc/g` | **Literal Pattern + flag** | Glob(find all matches) |
| `/abc/i` | **Literal Pattern + flag** | Case-insesitive match |
| `[0-9]` | **Literal Pattern| Match ONE digit 0–9 |
| `[A-F0-9]` | **Literal Pattern| Match ONE hexadecimal digit |
| `[\w\d]` | **Literal Pattern| Match ONE word character or digit |
|`[e3]`| Example |Match ONE character either e or 3|
|`(?:^|\s)`|Example | Matches a space or the start/beginning of the string|
|`(?:$|\s)`|Example | Matches a space or the end of the string|
|/^\s*$/|Blank Input|Is the entire input blank or only whitespace|
||^ |position begin matching at start of Input|
||\s* |   zero or more whitespace characters|
||$ |postion stop matching at end of Input|

Examples:
const helpRegex = /please help|assist me/i;</br>
const dollarRegex = /[0-9]+\s*(?:hundred|thousand|million|billion)?\s+dollars/i;</br>
const freeRegex = /(?:^|\s)fr[e3][e3] m[o0]n[e3]y(?:$|\s)/i;</br>
const stockRegex = /(?:^|\s)[s5][t7][o0][c{[(]k [a@4]l[e3]r[t7](?:$|\s)/i;</br>
const dearRegex = /dear friend/i;</br>

---
## **2. Regex Flags (Modifiers)**  
FLAGS appear *after* the closing/final slash: `/pattern/flags`

| Flag | Name | Meaning |
|------|------|---------|
| `i` | **Ignore Case** | Case‑insensitive matching |
| `g` | **Global** | Find **all** matches, not just the first |
| `m` | **Multiline** | `^` and `$` match per line |
| `s` | **DotAll** | `.` matches newline |
| `u` | **Unicode** | Enables full Unicode support |
| `y` | **Sticky** | Match must start at `lastIndex` |
| `d` | **Indices** | Return start/end indices of matches |
| `v` | **Extended Unicode** | Advanced Unicode class(newJS) |
---
# **🔥 Important Clarification**
These are **not flags**:

- `.`
- `\w`
- `+`
- `*`
- `?`
- `[abc]`

They are **tokens**, **quantifiers**, or **character classes**.

## **3. Anchors (these DO NOT match characters — they match positions)**
- 'word character' (\w ) - a-z, A-Z, 0-9, _ ;
- 'Non-word character' (space, punct, symbols)

| Token |Name|Meaning |example|
|-------|---------|--------|------|
| `^` |position|Only at start of string| /^[cC]/-->cat Car cart dog= Matches only cat|
| `$` |position|only at end of string |/cat$/--> Matches 'copycat' not 'category'|
|^ and $ |combined|Match exact word|/^hello$/--> Matcches 'hello' not 'hello world'|
| `\b` |word boundary `edge` |Match any word that begin with what follows|/\b[cC]/--> Match anyword begin with C c anywhere in string|
| `\B` | not a word‑boundary `inside`|Match anywhere in the middle|/\Bcat/--> Matches 'cat' in education|

---
## **4. Quantifiers (these modify how many characters to match)**

| Token |Name | Meaning |
|-------|---------|----------|
| `*` |**Zero‑or‑More Quantifier** | Match 0 or more of the previous token |
| `+` |**One‑or‑More Quantifier** | Match 1 or more of the previous token |
| `?` |**Optional Quantifier** | Match 0 or 1 of the previous token |
| `{n}` | Match exactly n occurrences |
| `{n,}` | Match n or more occurrences |
| `{n,m}` | Match between n and m occurrences |
|`/^#{1.3}$/`|Match a string that contains only 1 - 3 # characters|
|`/^#{1.3}$/`|Means same|
---
## **5. Grouping & Alternation (these do NOT match characters by themselves)**

| Token | Meaning |
|-------|---------|
| `(abc)` | Capture the group “abc” |
| `(?:abc)` | Non‑capturing group |
| `a\|b` | Match a OR b |
| `(a\|b\|c)` | Match one of a, b, or c |

---
## **6. Escaped Literals (these MATCH literal characters)**

| Token | Meaning |
|-------|---------|
| `\.` | Match a literal dot `.` |
| `\*` | Match a literal asterisk `*` |
| `\+` | Match a literal plus `+` |
| `\?` | Match a literal question mark `?` |
| `\(` `\)` | Match literal parentheses |
| `\[` `\]` | Match literal brackets |
| `\\` | Match a literal backslash |

---
## **7. Unicode Property Classes (these MATCH characters)**  
*(Requires `u` flag)*

| Token | Meaning |
|-------|---------|
| `\p{L}` | Match any letter |
| `\p{N}` | Match any number |
| `\p{P}` | Match punctuation |
| `\p{S}` | Match symbol |
| `\p{Z}` | Match separator |
| `\p{Ll}` | Match lowercase letter |
| `\p{Lu}` | Match uppercase letter |

Example:

```js
/\p{L}/u
```
---
## **8. Lookarounds (these do NOT match characters — they assert conditions)**

| Token | Meaning |
|-------|---------|
| `(?=...)` | Positive lookahead |
| `(?!...)` | Negative lookahead |
| `(?<=...)` | Positive lookbehind |
| `(?<!...)` | Negative lookbehind |
---
# **Match & Replace All Occurrences**

## **9. Default Behavior (Without global `g` Flag)**

- `match()` → returns **only the first match**
- `replace()` → replaces **only the first occurrence**

```js
const regex = /outDoorCamp/;
str.match(regex);     // first match only
str.replace(regex, "outDoorCamp"); // replaces first only
```
# **10. Using the `g` (Global) Flag**
Add `g` to match **all occurrences**.

```js
const regex = /outDoorCamp/g;
str.match(regex);     // ['outDoorCamp', 'outDoorCamp']
str.replace(regex, "outDoorCamp");
// "outDoorCamp is the best we love outDoorCamp"
```

✔ `g` + `match()` returns **an ARRAY of all matches**  
✔ `g` + `replace()` replaces **every occurrence**

⚠ With `.test()`, `g` makes the regex **stateful** (`lastIndex` moves).

---

# ✅ **Meaning of `/[###]/`**

Inside a regex, square brackets `[...]` define a **character class**.

> “Match choose **one** character from this set.”

So:

```
/[###]/ equal to /[#]/ or /#/
```
# 🔍 `[###]` means “choose one character from this list.”

# 🧠 Summary

| Pattern | Meaning |
|--------|---------|
| `[###]` | match **one** of these characters `#` |
| `###` | match the literal string `"###"` |
| `#{3}` | match exactly **three** `#` characters |












































---
# JAVASCRIPT-REGEX-Regular-Expressions

## **What Are Regular Expressions (REGEX)?**
- 2 ways to create regular expresions
    1. literal notation use a regex wrapper, slashes for start and end
               - '/pattern/'
    2. RegExp constructor new RegExp('pattern')

## **1. How to Write REGEX expresions PATTERN
A. Simple Pattern </br>
    - /cat/ Matches 'cat', 'category', 'copycat'</br>
B. Special Characters</br>
- enhance pattern matching</br>
- character * matches zero or more of preceding item.</br>
    
C. or Combine simple pattern with characters</br>
- /ab*c/ matches "ac", "abc", "abbc",</br>

#### A. Simple Pattern
- Match **exact CHARACTERS between slashes** used to search, test, extract, and replace text.

```js
const regex = /outDoorCamp/;
```
## **2. Combine Regex with Methods**
- Methods for RegExp and String objects
**Methods have 2 syntax**
- regex.methodname(string)
- string.methodname(regex)

### **A. `test()`** to check string
-Does this **STRING MATCH THE REGEX** or pattern.
- Returns **true/false**.

```js
regex.methodname(string)
/abc/.test("abc");        // true
/abc/.test("I love abc"); // true
/abc/.test("ab");         // false
```
### **a. `some()`** to check array
- Belongs to Array not RegExp
- Does at least one element in array satisfy a condition

- ```js
["a", " ", "b"].some(char => char === " ")
// true
```

### **B. `exec()`**
- Searches for pattern within a string.
- It returns an array with details,

### **C. `match()`**
- Searches for 1st occurance of pattern in String
- Returns 1st element in **array** if match or **null** if no match.
- To match all occurances use global flag (g) 

```js
string.methodname(regex)
"outDoorCamp".match(/outDoorCamp/);
// ['outDoorCamp', index: 0, input: 'outDoorCamp', groups: undefined]
```

**Array includes:**
- the matched text  
- `index` → where the match starts  
- `input` → original string  
- `groups` → captured groups (if any)

### **C.a `matchAll()`**
- Returns an iterator of all pattern matches against a string.
- EACH ELEMENT of the iterator is an array containing details about the match
- **BEST WHEN** you need detailed information about all matches in a string.
```js
let str = "Hello world! This is a test string.";
let regex = /[a-zA-Z]+/g;

let matches = str.matchAll(regex);

for (let match of matches) {
    console.log(match);
}
[ 'Hello', index: 0, input: 'Hello world! This is a test string.', groups: undefined ]
[ 'world', index: 6, input: 'Hello world! This is a test string.', groups: undefined ]
ETC...
```

### **D. `replace()`**
- Replaces matched text with new text.
- To replace all occurances use global flag (g)

```js
string.methodname(regex)
"freecodecamp is cool"
  .replace(/freecodecamp/, "freeCodeCamp");
// "freeCodeCamp is cool"
```
### **D.a `replaceAll()`**
- Replaces all occurrences of a pattern with a string.

```js
let str = "apple,banana,apple,grape";
let newStr = str.replaceAll("apple", "orange");
console.log(newStr);
// Output: "orange,banana,orange,grape"
```
### **E. `search()`**
- Searches a pattern within a string and returns the INDEX of the first occurrence or -1 if not found.

```js
let str = "The quick brown fox jumps over the lazy dog";
let pattern = /brown/;

let result = str.search(pattern);
console.log(result); // Output: 10
```
## **3. Key Behaviors**

### **Regex ix Case‑Sensitive**
```js
regex.methodname(string)
/freeCodeCamp/.test("freecodecamp"); // false
```

### **Must Match Entire Pattern**
- Partial matches don’t pass.

```js
/freeCodeCamp/.test("free"); // false
```
## **4. Quick Reference Table**

| Method | Called On | Argument | Returns | Purpose |
|--------|-----------|----------|---------|---------|
| `test()` | RegExp | string | boolean | Check if pattern exists |
| `match()` | string | RegExp | array or null | Get match details |
| `replace()` | string | RegExp or string | new string | Replace matched text |
---

# **🔥 JavaScript Regex vs String Methods — Comparison Table**

## **1. RegExp Object Methods (regex.method(string))**

| Method | Called On | Argument | Returns | Best Use Case |
|--------|-----------|----------|---------|----------------|
| **`regex.test(string)`** | RegExp | string | **Boolean** (`true`/`false`) | Checking if a pattern exists (validation) |
| **`regex.exec(string)`** | RegExp | string | **Array** with match + groups + index, or **null** | Extracting data, iterating through multiple matches with `g` |

---

## **2. String Methods (string.method(regex))**

| Method | Called On | Argument | Returns | Best Use Case |
|--------|-----------|----------|---------|----------------|
| **`string.match(regex)`** | String | RegExp | Array or null | Simple matching; with `g` → array of all matches |
| **`string.search(regex)`** | String | RegExp | Index or -1 | Finding the position of the first match |
| **`string.replace(regex, replacement)`** | String | RegExp or string | New string | Replacing text (first match unless `g`) |
| **`string.split(regex)`** | String | RegExp | Array of substrings | Splitting text using a pattern |

---

# **🔥 Quick Summary (One‑Liners)**

- **`test()`** → “Does it match?”  
- **`exec()`** → “Give me the match details.”  
- **`match()`** → “Give me matches from the string.”  
- **`search()`** → “Where is the first match?”  
- **`replace()`** → “Swap matched text with something else.”  
- **`split()`** → “Cut the string wherever this pattern appears.”
---


# **Regular Expression Modifiers (Flags) **

## **What Are Modifiers?**
- Modifiers (or flags) change **how** a regex searches.  
- Come **after** the closing slash:

```js
/outDoorCamp/i
```

# **1. `i` — Case‑Insensitive**
- `i` Makes Regex IGNORE CASE.
✔ Used to match text regardless of capitalization

```js
/outDoorCamp/i.test("OUTDOORCAMP"); // true
/outDoorCamp/i.test("outdoorcamp"); // true
```

# **2. `g` — Global Search**
- Finds **ALL MATCHES** not just the first.

```js
"outDoorCamp outDoorCamp".match(/outDoorCamp/gi);
// ['outDoorCamp', 'outDoorCamp']
```

⚠ **Important:**  
`g` makes regex **stateful** when using `.test()`:
- It remembers where the last match ended (`lastIndex`)
- It can cause unexpected **true/false** results when testing multiple strings

```js
const r = /outDoorCamp/gi;
r.test("outDoorCamp"); // true
r.test("outDoorCamp is great"); // false (starts searching from lastIndex)
```

✔ Use `g` when matching **multiple occurrences in one string**  
✘ Avoid `g` when testing **multiple different strings**
---

# **3. `m` — Multiline Mode**
- Makes `^` and `$` match the **start/end of each line**, not the whole string.

```js
/^outDoorCamp/m.test("hello\noutDoorCamp\nworld"); // true
/outDoorCamp$/m.test("hello\noutDoorCamp");        // true
```

✔ Useful for multi‑line text blocks.

---

# **4. Anchors (Used With Flags)**
- Represent postition not characters in a string

| Main Anchors | Meaning |
|--------|---------|
| `^` | Match start of string/line |
| `$` | Match end of string/line |

Examples:

```js
/^outDoorCamp/i.test("outDoorCamp rules"); // true
/outDoorCamp$/i.test("I love outDoorCamp"); // true
```

---

# **5. `d` — Indices Flag**
- Gives an array with the **start and end positions** of the match.

```js
"we love outDoorCamp".match(/outDoorCamp/di);
// indices: [ [8, 20] ]
```
---

# **6. `u` — Unicode Mode**
Enables full Unicode support (emoji, special characters).

```js
/🍎/u.test("I have an apple 🍎"); // true
```
---

# **7. `y` — Sticky Mode**
Like `g`, but **must match exactly at `lastIndex`**.

```js
const r = /outDoorCamp/y;
r.lastIndex = 5;
r.test("xxxxxoutDoorCamp"); // true only if match starts at index 5
```
✔ Precise control over match position.

---

# **8. `s` — Single‑Line Mode**
Makes `.` match **newlines**.

```js
/outDoorCamp.world/s.test("outDoorCamp\nworld"); // true
```
✔ Useful when scanning multi‑line text as one block.

---




# **3. matchAll() — Modern, Powerful Matching**
`matchAll()` returns an **iterator NOT ARRAY** with details of index, input, groups.

Requires the **global flag**:

```js
const regex = /outDoorCamp/g;
const matches = str.matchAll(regex);
```

### Convert iterator → array:
```js
Array.from(matches);
```

Result includes:
- matched text  
- index  
- input  
- groups  

---

# **4. replaceAll() — Replace Everything Easily**
`replaceAll()` replaces **every** occurrence without needing regex.

```js
str.replaceAll("outDoorCamp", "outDoorCamp");
```

Works with regex too (must include `g`):

```js
str.replaceAll(/outDoorCamp/g, "outDoorCamp");
```

---

# **5. matchAll() Iterator Behavior**
`matchAll()` is **lazy**:

- Finds the next match **only when `.next()` is called**
- Stops *ONLY* when `.next()` returns `{ done: true }`

Example:

```js
const it = str.matchAll(/outDoorCamp/g);
it.next(); // first match
it.next(); // second match
it.next(); // done: true
```
Here’s a **tight, classroom‑ready condensed version**, NAFIZ:

---

# **Explanation**

As long as `matchAll()` keeps finding matches, the iterator continues. When it finally fails to find another match, it returns `{ done: true, value: undefined }`.

To avoid manually calling `.next()` repeatedly, convert the iterator into an array at once using:

```js
Array.from(iterator)
```

This gives you all matches immediately, without the lazy step‑by‑step iteration.
---

# **6. Summary Table**

| Method | Needs `g`? | Returns | Finds All? | Notes |
|--------|------------|---------|------------|-------|
| `match()` | No | array or null | ❌ | Only first match |
| `match()` + `g` | Yes | array of matches | ✔ | Loses index info |
| `matchAll()` | Yes | iterator | ✔ | Full match details |
| `replace()` | No | new string | ❌ | Replaces first only |
| `replace()` + `g` | Yes | new string | ✔ | Replaces all |
| `replaceAll()` | Yes (if regex) | new string | ✔ | Easiest full replace |

---

# **Character Classes**

## **What Are Character Classes?**
- Character classes let you match **sets** of characters instead of writing each one manually.
- Create a character class with square brackets which matches any character within the [a list];

---

## **1. Wildcard (`.`)**
- Matches **any single character** except line breaks  
- Use the **`s` flag** to include line breaks

```js
/a./   // matches "a" + any character
```

---

## **2. Shorthand Character Classes**
| Class | Matches |
|-------|---------|
| `\d` | any digit (0–9) |
| `\w` | letters, digits, underscore |
| `\s` | whitespace (space, tab, newline) |

### **Negated versions**
Use uppercase to mean “NOT”:

| Class | Matches |
|-------|---------|
| `\D` | do not match a digit |
| `\W` | do not match a word character |
| `\S` | do not match whitespace |

---

## **3. Custom Character Classes (`[...]`)**
- USE selector `[]` the `[range]` within selector
- Selector `[ ]` says Match **one character** from this range or list:
 
```js
/[abcdf]/   // A, B, C, D, or F
//Match ONE character that is either a, b, c, d, or f.”
```

### **Ranges**
Use hyphens for consecutive characters:

```js
/[a-d]/     // a, b, c, d
/[0-9]/     // digits
/[a-zA-Z]/  // all letters
```

### **Mixing types**
```js
/[a-zA-Z0-9]/   // letters + digits (like \w but no underscore)
```

### **Literal Character 
**
- When `-` hyphen placed at the **start or end**:

```js
/[-a-z]/
“Match 1 character: either a hyphen - OR any lowercase letter from a-z.”
Matches - or a or b or c...z
---

## **4. Combining Classes**
You can include shorthand classes inside custom ones:

```js
/[-\w]/   // word characters + hyphen
```

## **Key Idea**
Character classes give you **precise control** over what characters your regex should accept or reject.

---

# **Lookaheads & Lookbehinds**

Lookaheads and lookbehinds let you match something **only if** it *is* or *is not* next to another pattern. They check surrounding text **without including it** in the match.

---

## **1. Positive Lookahead — `(?=...)`**
Match **X only if it is followed by Y**.

```js
/outDoor(?=Camp)/i   // match "outDoor" only when followed by "Camp"
```

---

## **2. Negative Lookahead — `(?!...)`**
Match **X only if it is NOT followed by Y**.

```js
/outDoor(?!Camp)/i   // match "outDoor" not followed by "Camp"
```

---

## **3. Positive Lookbehind — `(?<=...)`**
Match **X only if it is preceded by Y**.

```js
/(?<=outDoor)Camp/i   // match "Camp" only when preceded by "outDoor"
```

---

## **4. Negative Lookbehind — `(?<!...)`**
Match **X only if it is NOT preceded by Y**.

```js
/(?<!outDoor)Camp/i   // match "Camp" not preceded by "outDoor"
```

- `test()` only tells you **whether** a match exists true/false not the match.  
- `match()` with a negative lookbehind like `/(?<!out)door/` shows **matched text**.  
- Regex `/(?<!out)door/` checks whether **“door” is NOT preceded by “out”**, but it **does not include “out”** in the match.  
- When “door” *is* preceded by “out,” `match()` returns **null**.  
- When “door” is *not* preceded by “out,” `match()` returns **only `"dooe"`**, with index and input string.

---

## **Key Idea**
Lookaheads and lookbehinds **peek** at surrounding text but **don’t consume it** — the match result includes only the main pattern (outDoor or Camp), not the condition.

---

# **Regex Quantifiers — Summary**

- Quantifiers let you specify **how many times** a pattern should repeat.
- Instead of writing `\d\d\d\d`, you can use a quantifier: `\d{4}`.

---

## **Curly‑Brace Quantifiers**
- **`{n}`** → match **exactly n** times  
  - `\d{4}` matches exactly four digits.
- **`{n,}`** → match **n or more** times  
  - `\d{4,}` matches 4+ digits.
- **`{n,m}`** → match **between n and m** times  
  - `\d{4,6}` matches 4 to 6 digits.
- You **cannot** specify only a maximum (e.g., `{,6}` is invalid).  
  - Use `{1,6}` instead.

---

## **Shorthand Quantifiers**
- **`?`** → match **0 or 1** (optional)  
  - `[A-Z]?` = optional letter.
- **`*`** → match **0 or more**  
  - `[A-Z]*` = any number of letters.
- **`+`** → match **1 or more**  
  - `[A-Z]+` = at least one letter.
  - 
“Optional letter” =
“There may be a letter here, but it’s okay if there isn’t.”

---

## **Examples**
- Optional single letter + 4–6 digits:  
  - `/^[A-Za-z]?\d{4,6}$/`
  - “Match a string that may start with one letter, followed by 4 to 6 digits.”
  - ^ start of string
  - [A-Z]? - one optional letter, so may appear once or not at all
  - Optional
  - both work...A1234 (letter present) or 1234 (letter missing)
  - \d{4,6} - match 4 to 6 digits
  - $ end of string
- Zero or more letters + 4–6 digits:  
  - `/^[A-Za-z]*\d{4,6}$/`
  - “A string that has any number of letters (or no letters), followed by 4 to 6 digits, and nothing else.”
- One or more letters + 4–6 digits:  
  - `/^[A-Za-z]+\d{4,6}$/`
  - “A string that begins with at least one letter,
  - followed immediately by 4 to 6 digits,
  - with nothing else before or after.”
  - [A-Za-z]+
  - So, start with at least one letter not zero letters
  - 1234 and !abc don't work
  - \d{4,6}
  - After letters have 4, 5, or 6 digits
  - 1 letter and 3 digits does not work A123
  - `^...$`
  - start with letters and end with digits

---

## **Key Idea**
Quantifiers make regex **shorter, clearer, and more flexible**, letting you control repetition without writing the same pattern multiple times.

---

# **Capturing Groups & Backreferences **

A **capturing group** is created by putting part of a regex inside parentheses:

```js
(code)
```
Which states:

**“Grab this part of the match and store it so I can use it later.”**
---

# **Why this matters in your example**

You wrote:

> *“Let's capture the Door from our outDoorCamp regular expression.”*

```js
/out(Door)camp/
```
- Match the word **out**
- Capture the exact text **Door**
- Then match **camp**

When you run:

```js
"outDoorcamp".match(/out(Door)camp/)
```
- Index 0 → `"freecodecamp"` (the whole match)
- Index 1 → `"code"` (the captured group)
 
**Capturing groups let you extract or reuse specific parts of what you matched.**

---

### **Capturing Groups**
- Parentheses `( )` captures part of a matched string.
- Example: `/out(door)camp/` would capture `"door"`.
- `match()` shows captured groups as extra array elements.
- Capturing groups store **patterns**, not character classes.

---

### **Using Captured Groups in `replace()`**
- You can reuse captured text in a replacement string.
- $ is used in replace() for backreference with # of the captured group
- `$1`, `$2`, etc. refer to the 1st, 2nd, etc. capture group.
- Example:  
  `"outdoooorcamp".replace(/our(do+or)camp)/, "paid$1world")`  
  → preserves the exact number of repeated letters.
- Find ‘out…camp’, 1st capture group the ‘do+or’ part (with all its o’s), and replace the whole thing with ‘paid + the captured part + world’.”
- out + doooor + camp
- so outdoooorcamp ---> paiddoooorworld

---

### **Backreferences Inside Regex**
- You can require the same captured text to appear again.
- Use `\1`, `\2`, etc. to reference earlier groups.
- Example:  
  `/out(do+or)camp.*out\1camp/`  
  → second “door” must have the **same number of a’o** as the first.

---

### **Named Capture Groups**
- Syntax: `(?<name>pattern)`
- Named backreference in regex: `\k<name>`
- Named backreference in replace: `$<name>`
---

### **Non‑Capturing Groups**
- Syntax: `(?:pattern)`
- Groups patterns **without capturing** them.
- Useful for OR patterns like:  
  `/out(?:door|trail)camp/`
---
> *“A non‑capturing group does not store the code|candy match separately in memory. But it can be helpful for creating alternate patterns without sacrificing readability or performance.”*

### **MEANING:**
- **Non‑capturing group** `(?: ... )` groups patterns **but don't save the match**.
- When parentheses are used **only for structure**, not for capturing.
- This keeps your regex **cleaner**, **faster**, and avoids creating unnecessary `$1`, `$2`, etc.

### **Example:**

```js
/free(?:code|candy)camp/
```
This matches:
- `freecodecamp`
- `freecandycamp`

…but **does not** store `"code"` or `"candy"` as a captured group.

---







___________________________________________________________
___________________________________________________________

# **🔥 Ultra‑Condensed Regex Master Summary **
___________________________________________________________
___________________________________________________________

## **1. What Regular Expressions Are**
- A **pattern‑matching syntax** for searching, testing, extracting, and replacing text.
- Written between slashes: `/pattern/`.

---

# **2. Core Regex Methods**

### **`test()`**
- Checks if a pattern exists → **true/false**.

### **`match()`**
- Returns **array** (match details) or **null**.

### **`replace()`**
- Replaces **first** match unless `g` is used.

### **`matchAll()`**
- Requires `g`.  
- Returns **iterator** with full match details.

### **`replaceAll()`**
- Replaces **every** occurrence (string or regex with `g`).

---

# **3. Key Behaviors**
- Regex is **case‑sensitive** by default.  
- Must match the **entire pattern** .

---

# **4. Basic Syntax**
| Pattern | Meaning |
|--------|---------|
| `/abc/` | literal match |
| `/abc/i` | ignore case |
| `/abc/g` | global |
| `.` | any character |
| `\d` | digit |
| `\w` | word char |
| `+` | one or more |
| `*` | zero or more |
| `?` | optional |

---

# **5. Flags (Modifiers)**

| Flag | Name | Effect |
|------|------|--------|
| **i** | Ignore Case | Case‑insensitive |
| **g** | Global | Find all matches; stateful `.test()` |
| **m** | Multiline | `^` and `$` match per line |
| **s** | Single‑line | `.` matches newlines |
| **y** | Sticky | Must match at `lastIndex` |
| **u** | Unicode | Full Unicode support |
| **d** | Indices | Start/end index ranges |

---

# **6. Anchors**
| Anchor | Meaning |
|--------|---------|
| `^` | start of string/line |
| `$` | end of string/line |

---

# **7. Character Classes [...]**
- Match `ONE CHARACTER` from a set.

### **Wildcard (`.`)**
- Any single character (except newline unless using `s`).

### **Shorthand Classes**
| Class | Matches |
|-------|---------|
| `\d` | digit |
| `\w` | letters, digits, underscore |
| `\s` | whitespace |

### **Negated Versions**
| Class | Matches |
|-------|---------|
| `\D` | NOT a digit |
| `\W` | NOT a word char |
| `\S` | NOT whitespace |

### **Custom Classes `[ ... ]`**
- Match **one** character from a set.
- Written with square brackets
- [abc] similar to (a|b|c)--> Match a, b, or c just one of them

Examples:
- `[abc]` → a, b, or c  
- `[a-z]` → lowercase letters
- `[0-9]` → digits
- `[a-zA-Z0-9]` → alphanumeric  
- `[-a-z]` → literal hyphen included  

### **Mixing**
- You can include shorthand inside:  
  `/[-\w]/`

---

# **8. Lookaheads & Lookbehinds**

### **Positive Lookahead `(?=...)`**
Match X **only if followed by** Y.  
`/outDoor(?=Camp)/`

### **Negative Lookahead `(?!...)`**
Match X **only if NOT followed by** Y.  
`/outDoor(?!Camp)/`

### **Positive Lookbehind `(?<=...)`**
Match X **only if preceded by** Y.  
`/(?<=outDoor)Camp/`

### **Negative Lookbehind `(?<!...)`**
Match X **only if NOT preceded by** Y.  
`/(?<!outDoor)Camp/`

**Key Idea:**  
Lookarounds **peek** at surrounding text but **don’t consume it**.

---

# **9. Quantifiers**

### **Curly‑Brace Quantifiers**
- `{n}` → exactly n  
- `{n,}` → n or more  
- `{n,m}` → between n and m  

### **Shorthand Quantifiers**
- `?` → 0 or 1 (optional)  
- `*` → 0 or more  
- `+` → 1 or more  

### **Examples**
- Optional letter + 4–6 digits:  
  `/^[A-Za-z]?\d{4,6}$/`
- Zero or more letters + digits:  
  `/^[A-Za-z]*\d{4,6}$/`
- One or more letters + digits:  
  `/^[A-Za-z]+\d{4,6}$/`

---

# **10. Capturing Groups & Backreferences**

### **Capturing Groups `( ... )`**
- Store part of the match for reuse.  
- `match()` returns captured groups as extra array items.

### **Backreferences in Replace**
- `$1`, `$2`, etc.  
- `"text".replace(/(do+or)/, "paid$1world")`

### **Backreferences in Regex**
- `\1`, `\2`, etc.  
- `/out(do+or)camp.*out\1camp/`

### **Named Groups**
- `(?<name>pattern)`  
- Backreference: `\k<name>`  
- Replace: `$<name>`

### **Non‑Capturing Groups `(?: ... )`**
- Grouping **without** capturing.  
- Useful for OR patterns:  
  `/out(?:door|trail)camp/`

**Key Idea:**  
Capturing groups extract or reuse text; non‑capturing groups organize patterns without storing anything.

---

# **11. Method Comparison Table**

| Method | Needs `g`? | Returns | Finds All? | Notes |
|--------|------------|---------|------------|-------|
| `test()` | No | boolean | ❌ | Existence check |
| `match()` | No | array/null | ❌ | First match |
| `match()` + `g` | Yes | array | ✔ | No index info |
| `matchAll()` | Yes | iterator | ✔ | Full details |
| `replace()` | No | string | ❌ | First only |
| `replace()` + `g` | Yes | string | ✔ | Replaces all |
| `replaceAll()` | Yes (regex) | string | ✔ | Simplest |

---

If you want, I can now turn this into:

- a **1‑page printable cheat sheet**,  
- **micAbsolutely, NAFIZ — I’ve folded **all** your new material (Character Classes, Lookarounds, Quantifiers, Capturing Groups, Backreferences, Non‑Capturing Groups) into the **Ultra‑Condensed Regex Summary** you asked me to build.  

Here is the **fully updated, clean, classroom‑ready master summary** — still tight, still structured, still optimized for print and teaching.

---

# **🔥 Ultra‑Condensed Regex Master Summary (Updated)**

## **1. What Regular Expressions Are**
- A **pattern‑matching language** for searching, testing, extracting, and replacing text.
- Written between slashes: `/pattern/`.

---

# **2. Core Regex Methods**

### **`test()`**
- Checks if a pattern exists → **true/false**.

### **`match()`**
- Returns **array** (match details) or **null**.

### **`replace()`**
- Replaces **first** match unless `g` is used.

### **`matchAll()`**
- Requires `g`.  
- Returns **iterator** with full match details.

### **`replaceAll()`**
- Replaces **every** occurrence (string or regex with `g`).

---

# **3. Key Behaviors**
- Regex is **case‑sensitive** by default.  
- Must match the **entire pattern**.

---

# **4. Basic Syntax**
| Pattern | Meaning |
|--------|---------|
| `/abc/` | literal match |
| `/abc/i` | ignore case |
| `/abc/g` | global |
| `.` | any character |
| `\d` | digit |
| `\w` | word char |
| `+` | one or more |
| `*` | zero or more |
| `?` | optional |

---

# **5. Flags (Modifiers)**

| Flag | Name | Effect |
|------|------|--------|
| **i** | Ignore Case | Case‑insensitive |
| **g** | Global | Find all matches; stateful `.test()` |
| **m** | Multiline | `^` and `$` match per line |
| **s** | Single‑line | `.` matches newlines |
| **y** | Sticky | Must match at `lastIndex` |
| **u** | Unicode | Full Unicode support |
| **d** | Indices | Start/end index ranges |

---

# **6. Anchors**
| Anchor | Meaning |
|--------|---------|
| `^` | start of string/line |
| `$` | end of string/line |

---

# **7. Character Classes**
- All types of character classes match just a **`SINGLE CHARACTER`**

### **Wildcard (`.`)**
- Any single character (except newline unless using `s`).

       [0-9]   // custom class
       \d      // shorthand class
- Both match a single digit.


### **Shorthand Classes**
| Class | Matches |
|-------|---------|
| `\d` | digit |
| `\w` | letters, digits, underscore |
| `\s` | whitespace |

### **Negated Versions**
| Class | Matches |
|-------|---------|
| `\D` | NOT a digit |
| `\W` | NOT a word char |
| `\S` | NOT whitespace |

### **Custom Classes `[ ... ]`**
- Match **one** character from a set **`THAT YOU DEFINE`**.

Examples:
- `[abc]` → a, b, or c  
- `[a-z]` → lowercase letters  
- `[a-zA-Z0-9]` → alphanumeric  
- `[-a-z]` → literal hyphen included  

### **Mixing**
- You can include shorthand inside:  
  `/[-\w]/`

---

# **8. Lookaheads & Lookbehinds**

### **Positive Lookahead `(?=...)`**
Match X **only if followed by** Y.  
`/outDoor(?=Camp)/`

### **Negative Lookahead `(?!...)`**
Match X **only if NOT followed by** Y.  
`/outDoor(?!Camp)/`

### **Positive Lookbehind `(?<=...)`**
Match X **only if preceded by** Y.  
`/(?<=outDoor)Camp/`

### **Negative Lookbehind `(?<!...)`**
Match X **only if NOT preceded by** Y.  
`/(?<!outDoor)Camp/`

**Key Idea:**  
Lookarounds **peek** at surrounding text but **don’t consume it**.

---

# **9. Quantifiers**

### **Curly‑Brace Quantifiers**
- `{n}` → exactly n  
- `{n,}` → n or more  
- `{n,m}` → between n and m  

### **Shorthand Quantifiers**
- `?` → 0 or 1 (optional)  
- `*` → 0 or more  
- `+` → 1 or more  

### **Examples**
- Optional letter + 4–6 digits:  
  `/^[A-Za-z]?\d{4,6}$/`
- Zero or more letters + digits:  
  `/^[A-Za-z]*\d{4,6}$/`
- One or more letters + digits:  
  `/^[A-Za-z]+\d{4,6}$/`

---

# **10. Capturing Groups & Backreferences**

### **Capturing Groups `( ... )`**
- Store part of the match for reuse.  
- `match()` returns captured groups as extra array items.

### **Backreferences in Replace**
- `$1`, `$2`, etc.  
- `"text".replace(/(do+or)/, "paid$1world")`

### **Backreferences in Regex**
- `\1`, `\2`, etc.  
- `/out(do+or)camp.*out\1camp/`

### **Named Groups**
- `(?<name>pattern)`  
- Backreference: `\k<name>`  
- Replace: `$<name>`

### **Non‑Capturing Groups `(?: ... )`**
- Grouping **without** capturing.  
- Useful for OR patterns:  
  `/out(?:door|trail)camp/`

**Key Idea:**  
Capturing groups extract or reuse text; non‑capturing groups organize patterns without storing anything.

---

# **11. Method Comparison Table**

| Method | Needs `g`? | Returns | Finds All? | Notes |
|--------|------------|---------|------------|-------|
| `test()` | No | boolean | ❌ | Existence check |
| `match()` | No | array/null | ❌ | First match |
| `match()` + `g` | Yes | array | ✔ | No index info |
| `matchAll()` | Yes | iterator | ✔ | Full details |
| `replace()` | No | string | ❌ | First only |
| `replace()` + `g` | Yes | string | ✔ | Replaces all |
| `replaceAll()` | Yes (regex) | string | ✔ | Simplest |

---
