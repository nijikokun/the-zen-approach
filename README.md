# The Zen Approach
#### *By Nijiko Yonskai*

#### Preface

I'm no Zen Master.

I'm slowly learning how to be one however. In the beginning, I was rigid, like the trunk of a tree. Solid in my beliefs that what I did was the best; The only art in existence worth reading; Simplicity at it's finest; A styleguide for the ages was what my code was.

*I've learned that thinking like this is __extremely wrong__ on __multiple__ levels.*

Unlike me, JavaScript is more like the branches of the tree. It sways whatever way the wind blows. It goes with the flow; It does not really care how aesthetically pleasing you wish to make it. It gives you the flexibility that you need, and if you bend too far it breaks.

Being the trunk, you will always be underneath that flexibility. You have yet to understand and experience liberation. Even those branches are not liberated, the wind, that's the liberation you should strive for. The real flow. It doesn't even know the branches are there; but it moves them to it's will, not just this tree but any tree.

Becoming more like the wind, you must open your mind, cast aside any bias towards the black and white your mind controls you under and realize code more for it's ability to work, be performant, and at best consistent rather than how it appears.

Not only will you learn more, you'll be able to read the most difficult patterns; compact code; and begin experimenting, creating your own style, styleguide, and then finally realizing it's all bullshit and in a year or two what you like now will _completely_ change.

===

After working so closely with this language, JavaScript, for so many years (going on twelve now) these are some of my findings. Some items ramble on, others have concise points. Keep an open mind, and if you find something at fault; Please, open an issue. Thank you.

===

### General Tips

1. Avoid things that are inherently bad, or cause performance problems.
2. Find inspiration in the differences you have.
3. Learn from your mistakes, however small or big, admit them; It's okay, we all make them.
4. If it does not affect performance, or does not affect the outcome, it is aesthetic. 
   It cannot be right or wrong.
5. No trailing commas in lists or dictionaries (hash).
6. Use semi-colons, if only for your sanity.

===

### Natives

Do not extend them, in the end you will only find trouble. This path is narrow and crumbles beneath the feet quickly. Use caution when treading.

* I myself, many times before, have done this. I've learned from my mistakes that not everyone follows the age old rule of checking `hasOwnProperty` this is one of the biggest reasons you shouldn't do it.


Only invoke using Natives when you are building the following as they can only provide benefits in these situations:

1. Class Systems
2. Modular Extensions
3. Game Engines (Beware of `Array` in this situation for performance)
4. Complex Problems. (Think algorithms, machine learning, ai, modeling)

===

### Spaces or Tabs?

Ah. The age old argument. 

_Use what everyone else in your group is using._

If it is just you, use spaces. Tabs have proven to me time and time again to be a pain to work with, on my system I set tabs to two space (this is also what I code in using spaces; I have more room for code on one line), on repositories I see my code at a four space tab, this can create confusion for not only you, but others.

#### What about line length?

Unless you are writing a man page, stay within your editor viewport.

Man pages, a good length is somewhere around 60 ~ 80.

#### What about whitespace?

Good question, lets start with functions.

**Functions**

One space before parens (`()`) and before the brace (`{`).

```javascript
function noop (args, spaced, normally) {
  // Code goes here
}
```

This is for a few reasons, it's not because of preference:

1. Syntax Highlighters.
   Some highlighters and themes will only highlight arguments correctly under these conditions.
2. Consistency.
   You put a space after `function`, continue with the rest of the syntax.

**Objects**

One space after the property notation (`property:`)

```javascript
var example = {
  property: 'one'
};
```

**Arrays**

Up to you, never had any preference here. 

I generally just make sure the comma is attached to the previous item:

```javascript
var example = [1, 2, "three"];
```

===

### Primatives

Two types, `simple` and `complex`.

##### Simple

Direct access.

1. `String`
2. `Number`
3. `Boolean`
4. `null`
5. `undefined`

```javascript
var one = 1;
var two = one;

two = 2;

console.log(one, two); // 1, 2
```

##### Complex

Reference access.

1. `Array`
2. `Object`
3. `Function`

```javascript
var one = [1, 2];
var two = one;

two[0] = 2;

console.log(one[0], one[1]); // (2, 2)
```

This can help you and be your worst enemy in certain situations.

To understand more about why this happens read about allocation, pointers, and etc in other languages such as Java, C++, C, C# to get a notion of what is going on.

===

### Objects

**Always remember:** No trailing commas, code can break when you do this in some compilers.

If the thing you are building is not one of those above under the Natives list and is performance related, use `{}` over `Object`.

```
var example = {
  one: 1,
  two: 2
};

console.log(example.one);
```

#### Notation

**Use Bracket Notation:**

1. When using a variable.
2. When properties have spaces, or characters that are not allowed in dot notation.
3. When properties are reserved.

**Use Dot Notation**

1. In all other situations.

**Using reserved words**

If you use _reserved_ words on objects and attempt to access them through dot notation, your code will not work in older versions of `IE`.

```javascript
var example = {
  private: function () {}
};

// Can and will, break in older browsers.
example.private;

// Will work in older browsers.
// Acceptable, in my opinion only for the three situations I mentioned earlier.
example['private'];
```

====

### Arrays

**Always remember:** No trailing commas, code can break when you do this in some compilers.

If the thing you are building is not one of those above under the Natives list and is performance related, use `[]` over `Array`.

Should you need to tell the future, a pre-defined length, use `Array`.

```javascript
var example = ['one', 'two'];

console.log(example[0]);
```

Prefer native methods over complicated code. Such as `.push`, `.pop`, `.splice`, `.sort`, `.filter`, `.map` (where available; **node.js**), and `.slice`.

#### Cloning

Use `.slice` over iteration.

===

### Strings

Use `''` or `""` dependant on situation, just attempt to be consistent.

1. As a rule of thumb, generally I tend to use `""` when I know it may be long bodies of text or  is some sort of free-form string without regulations. Because it can contain `'` more likely than `"`.

```javascript
var slug = 'joe_biden'; // Slugs are restrictive, personally to be consistent, here I would use double quotes. It's just an example and you can still easily read / change it.
var name = "Joe Biden"; // Names can contain '
var biography = "Wouldn't it make more sense to be logical, and rational rather than precise and perfect? Nothing is perfect. I make mistakes, I'm human. I am Joe Biden.";
```

#### Multiline

Judgement call, the slowest known method is `[].join`. If you are building something that requires high performance __do not__ use `[].join`. It's not bad, it's just not performant.

The two fastest methods of multiline are one-line strings (no breaks), and in second using the `\` character (breaks), with `+` (concat) trailing slightly behind. [I'll let hard data back me up on this.](http://jsperf.com/ya-string-concat/10)

My personal preference is to use one line for performance (word-wrap exists people), and then `[].join` for non-performant things, like variables and such. Should the line require variables _and_ need to be performant I will use `+` concat notation.

```javascript
var preferences = "This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.";

var not_likely = "This is a super long error that was thrown because of Batman. \
When you stop to think about how Batman had anything to do with this, \
you would get nowhere fast.";

var more_likely = "This is a super long error that was thrown because of Batman. " +
  "When you stop to think about how Batman had anything to do with this, " +
  "you would get nowhere fast.";
```

===

### Variables

Always declare variables using `var`. Otherwise you're going to make a global, and pollute the namespace.

```javascript
var one = 1;
var two = "two";
var three =  1 * 3;
var four = function four () {
  return three + one;
};
```
Personally, I don't care how you set variables, the only rule of thumb I keep is the following:

1. Assigned first, un-assigned last.


After years of trying to find the _perfect_ style, I returned back to using multiple `var` statements for assigned variables, and multi-line for unassigned. 

**Why?** Simple reason: Nesting & Heirarchy. The code flows, easy to scan and read without losing context of where I am. Blocks that follow begin on the same line as the last variable.

It looks like this:

```javascript
var one = 1;
var two = 2;
var three = 3;
var four, five, six;
```

Looking at it now, I sort of feel like changing this and going to multiple `var` statements for un-assigned as well.

```javascript
var one = 1;
var two = 2;
var three = 3;
var four;
var five;
var six;
```

**Why?** Because, it would make it easier in the future should I remove assignment later and wish for it to be at the start of my block with minimal code change; That's the only reason, it doesn't have to do with aesthetics, or anything like how it looks.

Should I know that those assignments will always happen later, I do single line, should I think they could change (meaning I am unsure about the future) I do multi-line.

This only applies in my preference to un-assigned.

#### Other Styles

The first, is a common, in my opinion somewhat harder to scan list, when you are looking at it inside of code contextually; Without context it looks nice. The gap in the beginning causes visual problems for me personally when I start a block after it. Nesting and heirarchy get lost.

```javascript
// Single var statement, multiple variables, comma after, columnized.

var one = 1,
    two = 2,
    three = 3,
    four, 
    five, 
    six;
```

The following block, makes a little more sense, however it can be problematic with linting, and compilers. Notably older compilers. It gives you more of a visual seperation but you still lose sight of it quickly when inside context. Nesting and Heirarchy gets lost fast, just like the previous.

```javascript
// Single var statement, multiple variables, comma before.
// Can cause problems in some situations.

var one = 1
  , two = 2
  , three = 3
  , four
  , five
  , six;
```

There is also the single line, this is just hard to read after a certain point so I will skip it. Nobody really uses it, except short un-assigned lists.

## Todo

Things I have not glossed over, yet here are some quick snippets of information you may find useful right away.

1. **Naming conventions.** (Personally `+1` for snake, camel, and pascal, also going over leading `$` vs `_` and when to use them.)
2. **Private variables.** (Personally prefer **real** private variables over cheap hacks such as leading underscore.)
3. **Casting and Coercion.** (It's pretty cool, fun, and many people don't know it exists.)
4. **Comments**. (Personal Findings: Doc-blocks are cool for generation, single line are great for annotation, amazing code doesn't need much inline comments.)
5. **Blocks** (Don't create variables inside blocks as a general rule of thumb, unless performance. Generally, using braces _multi-line_ style is easier to read. Sometimes it's acceptable to ignore them.)
6. **Functions** (When to var, when not to var. Always name them for logging sake.)
