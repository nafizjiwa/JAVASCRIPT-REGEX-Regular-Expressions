# JAVASCRIPT-REGEX-Regular-Expressions

# **Regular Expressions (Regex) — Cheat Sheet**

## **1. What Are Regular Expressions?**
- A **pattern‑matching syntax** used to search, test, extract, and replace text.
- In JavaScript, regex is written between **slashes**:

```js
const regex = /freeCodeCamp/;
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
"freeCodeCamp".match(/freeCodeCamp/);
// ['freeCodeCamp', index: 0, input: 'freeCodeCamp', groups: undefined]
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
| `\d` | digit |
| `\w` | word character |
| `+` | one or more |
| `*` | zero or more |
| `?` | optional |

---

# **Regular Expression Modifiers (Flags) — Cheat Sheet**

## **What Are Modifiers?**
Modifiers (flags) change **how** a regex searches.  
They appear **after** the closing slash:

```js
/freeCodeCamp/i
```
---

# **1. `i` — Case‑Insensitive**
Makes the pattern ignore case.

```js
/freeCodeCamp/i.test("FREECODECAMP"); // true
/freeCodeCamp/i.test("freecodecamp"); // true
```

✔ Useful when matching text regardless of capitalization.

---

# **2. `g` — Global Search**
Finds **all** matches instead of stopping at the first.

```js
"free free".match(/free/g); // ['free', 'free']
```

⚠ **Important:**  
`g` makes regex **stateful** when using `.test()`:

- It remembers where the last match ended (`lastIndex`)
- This can cause unexpected **true/false** results when testing multiple strings

```js
const r = /free/gi;
r.test("free"); // true
r.test("free again"); // false (starts searching from lastIndex)
```

✔ Use `g` when matching **multiple occurrences in one string**  
✘ Avoid `g` when testing **multiple different strings**

---

# **3. `m` — Multiline Mode**
Makes `^` and `$` match the **start/end of each line**, not the whole string.

```js
/^free/m.test("hello\nfree\nworld"); // true
/free$/m.test("hello\nfree");        // true
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
/^free/i.test("freecodecamp"); // true
/free$/i.test("I love free");  // true
```

---

# **5. `d` — Indices Flag**
Adds an `indices` array showing the **start and end positions** of matches.

```js
"we love freecodecamp".match(/freecodecamp/di);
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
const r = /free/y;
r.lastIndex = 5;
r.test("xxx free xxx"); // true only if match starts at index 5
```

✔ Precise control over match position.

---

# **8. `s` — Single‑Line Mode**
Makes `.` match **newlines**.

```js
/hello.world/s.test("hello\nworld"); // true
```

✔ Useful when scanning multi‑line text as one block.

---

# **Summary Table**

| Flag | Name | Effect |
|------|------|--------|
| **i** | Ignore Case | Case‑insensitive matching |
| **g** | Global | Find all matches; stateful `.test()` |
| **m** | Multiline | `^` and `$` match per line |
| **s** | Single‑line | `.` matches newlines |
| **y** | Sticky | Match only at `lastIndex` |
| **u** | Unicode | Enables full Unicode support |
| **v** | Extended Unicode | More advanced Unicode classes |
| **d** | Indices | Adds match index ranges |

---

If you want, I can also create:
- a **visual diagram** showing how `lastIndex` moves with `g` and `y`
- a **student quiz version**
- a **micro‑card** that pairs with your other pocket sheets
