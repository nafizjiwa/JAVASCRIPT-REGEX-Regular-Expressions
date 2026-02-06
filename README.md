# JAVASCRIPT-REGEX-Regular-Expressions

## **1. What Are Regular Expressions?**
- A **pattern‑matching syntax** used to search, test, extract, and replace text.
- In JavaScript, regex is written between **slashes**:

```js
const regex = /outDoorCamp/;
```

---

## **2. Common Regex Methods**

### **A. `test()`**
- Checks if a string **matches** the pattern.
- Returns **true/false**.

```js
/abc/.test("abc");        // true
/abc/.test("I love abc"); // true
/abc/.test("ab");         // false
```

---

### **B. `match()`**
- Returns a **match array** if found.
- Returns **null** if no match.

```js
"outDoorCamp".match(/outDoorCamp/);
// ['outDoorCamp', index: 0, input: 'outDoorCamp', groups: undefined]
```

**Match array includes:**
- the matched text  
- `index` → where the match starts  
- `input` → original string  
- `groups` → captured groups (if any)

---

### **C. `replace()`**
- Replaces matched text with new text.

```js
"freecodecamp is cool"
  .replace(/freecodecamp/, "freeCodeCamp");
// "freeCodeCamp is cool"
```

---

## **3. Key Behaviors**

### **Case‑Sensitive by Default**
```js
/freeCodeCamp/.test("freecodecamp"); // false
```

### **Must Match Entire Pattern**
Partial matches don’t count unless the pattern allows it.

```js
/freeCodeCamp/.test("free"); // false
```

---

## **4. Quick Reference Table**

| Method | Called On | Argument | Returns | Purpose |
|--------|-----------|----------|---------|---------|
| `test()` | RegExp | string | boolean | Check if pattern exists |
| `match()` | string | RegExp | array or null | Get match details |
| `replace()` | string | RegExp or string | new string | Replace matched text |

---

## **5. Basic Regex Syntax**

| Pattern | Meaning |
|---------|---------|
| `/abc/` | literal match |
| `/abc/i` | case‑insensitive |
| `/abc/g` | global (find all matches) |
| `.` | any character |
| `m` | multi line |
| `\d` | digit |
| `\w` | word character |
| `+` | one or more |
| `*` | zero or more |
| `?` | optional |

---

# **Regular Expression Modifiers (Flags) **

## **What Are Modifiers?**
Modifiers (flags) change **how** a regex searches.  
They appear **after** the closing slash:

```js
/outDoorCamp/i
```

---

# **1. `i` — Case‑Insensitive**
Makes the pattern ignore case.

```js
/outDoorCamp/i.test("OUTDOORCAMP"); // true
/outDoorCamp/i.test("outdoorcamp"); // true
```

✔ Useful when matching text regardless of capitalization.

---

# **2. `g` — Global Search**
Finds **all** matches instead of stopping at the first.

```js
"outDoorCamp outDoorCamp".match(/outDoorCamp/gi);
// ['outDoorCamp', 'outDoorCamp']
```

⚠ **Important:**  
`g` makes regex **stateful** when using `.test()`:

- It remembers where the last match ended (`lastIndex`)
- This can cause unexpected **true/false** results when testing multiple strings

```js
const r = /outDoorCamp/gi;
r.test("outDoorCamp"); // true
r.test("outDoorCamp is great"); // false (starts searching from lastIndex)
```

✔ Use `g` when matching **multiple occurrences in one string**  
✘ Avoid `g` when testing **multiple different strings**

---

# **3. `m` — Multiline Mode**
Makes `^` and `$` match the **start/end of each line**, not the whole string.

```js
/^outDoorCamp/m.test("hello\noutDoorCamp\nworld"); // true
/outDoorCamp$/m.test("hello\noutDoorCamp");        // true
```

✔ Useful for multi‑line text blocks.

---

# **4. Anchors (Used With Flags)**

| Anchor | Meaning |
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
Adds an `indices` array showing the **start and end positions** of matches.

```js
"we love outDoorCamp".match(/outDoorCamp/di);
// indices: [ [8, 20] ]
```

✔ Great for text processing and highlighting.

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

# **Summary Table**

| Flags | Name | Effect |
|------|------|--------|
| **i** | Ignore Case | Case‑insensitive matching |
| **g** | Global | Find all matches; stateful `.test()` |
| **m** | Multiline | `^` and `$` match per line |
| **.** | Wildcard | match any one character except a newline|
| **s** | Single‑line | `s` helps `.` match newlines |
| **y** | Sticky | Match only at `lastIndex` |
| **u** | Unicode | Enables full Unicode support |
| **v** | Extended Unicode | More advanced Unicode classes |
| **d** | Indices | Adds match index ranges |

---

# **Match & Replace All Occurrences**

## **1. Default Behavior (Without global `g` Flag)**

- `match()` → returns **only the first match**
- `replace()` → replaces **only the first occurrence**

```js
const regex = /outDoorCamp/;
str.match(regex);     // first match only
str.replace(regex, "outDoorCamp"); // replaces first only
```

---

# **2. Using the `g` (Global) Flag**
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
Character classes let you match **sets** of characters instead of writing each one manually.

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
Match **one character** from a list:

```js
/[abcdf]/   // A, B, C, D, or F
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

### **Literal hyphen**
Place it at the **start or end**:

```js
/[-a-z]/  
```

---

## **4. Combining Classes**
You can include shorthand classes inside custom ones:

```js
/[-\w]/   // word characters + hyphen
```

---

## **Key Idea**
Character classes give you **precise control** over what characters your regex should accept or reject.

---

Absolutely, NAFIZ — here’s your **fully updated version** with **outDoor** and **Camp** replacing every instance of *free* and *code*. Clean, tight, and classroom‑ready.

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
- `match()` with a negative lookbehind like `/(?<!free)code/` shows **matched text**.  
- Regex `/(?<!free)code/` checks whether **“code” is NOT preceded by “free”**, but it **does not include “free”** in the match.  
- When “code” *is* preceded by “free,” `match()` returns **null**.  
- When “code” is *not* preceded by “free,” `match()` returns **only `"code"`**, with index and input string.

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
  - “A string that has any number of letters (including none), followed by 4 to 6 digits, and nothing else.”
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



