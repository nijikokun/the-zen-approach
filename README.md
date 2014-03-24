# The Zen Approach
#### *By Nijiko Yonskai*



## Table of Contents

1. [Foreword](#foreword)
2. [General Tips](#general-tips)
3. [Whitespace](#whitespace)
	1. [Tabs and Spaces](#tabs-and-spaces)
	2. [Line Length](#line-length)
	3. [Code](#code)
		1. Assignment
		2. Functions
		3. Objects
		4. Arrays
4. [Natives](#natives)
5. [Primitives](#primitives)
	1. [Simple](#simple)
	2. [Complex](#complex)
6. [Objects](#objects)
   1. [Notation](#notation)
7. [Arrays](#arrays)
   1. [Cloning](#cloning)
8. [Strings](#strings)
   1. [Multiline](#multiline)
9. [Variables](#variables)
   1. [Other Styles](#other-styles)
10. [TODO](#todo)
	
===

### Foreword

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


## Whitespace

Balance between code and space, offers much insight, however through many battles do we gain any knowledge.

#### Tabs and Spaces

Ah. The age old argument. 

1. _Use what everyone else in your group is using._
2. If you are the only one, try out spaces.

**Why not tabs?**

Tabs can be problematic when switching between environments, and different computers. This is also a benefit for them in some cases like large groups where many people have differing ideals and prefer different widths than others. Tabs can be set to a variable width in most editors making it very useful.

This feature though, can be a double-edged sword; What was once useful, when viewing code on a site such as github, you will always see the full tab width (`4` spaces). Which can create confusion when those who does not use full tabs scan code in places other than their editor.

Spaces unlike tabs remain at a constant regardless of the system you put them on. Two spaces here will be two spaces everywhere.

**Why not spaces?**

Basically, the opposite of tabs. Being constant, this means if someone in your group prefers `3` space and you are using `2` space. Someone is going to lose the argument, and be a bit jaded. Granted, whoever is joining the group, should just follow the rules above to avoid argument.

### Line Length

A man once told me a page, on this page he said, stay within your editor viewport.

1. For man pages, a good length is somewhere around 60 ~ 80.
2. For all other things, word-wrap exists.

### Code

The final frontier, where many come to put stake, and many rest in peace.

**Assignment**

Even spaces, one space after `var` or `let`, one space after the assignment, no space before the final semicolon.

```javascript
var hello = "world";
```

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

## Natives

Do not extend them, in the end you will only find trouble. This path is narrow and crumbles beneath the feet quickly. Use caution when treading.

* I myself, many times before, have done this. I've learned from my mistakes that not everyone follows the age old rule of checking `hasOwnProperty` this is one of the biggest reasons you shouldn't do it.


Only invoke using Natives when you are building the following as they can only provide benefits in these situations:

1. Class Systems
2. Modular Extensions
3. Game Engines (Beware of `Array` in this situation for performance)
4. Complex Problems. (Think algorithms, machine learning, ai, modeling)


## Primitives

Two types, `simple` and `complex`.

#### Simple

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

#### Complex

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

## Objects

**Always remember:** No trailing commas, code can break when you do this in some compilers.

If the thing you are building is not one of those above under the Natives list and is performance related, use `{}` over `Object`.

```javascript
var example = {
  one: 1,
  two: 2
};

console.log(example.one);
```

### Notation

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

## Arrays

**Always remember:** No trailing commas, code can break when you do this in some engines.

If the thing you are building is not one of those above under the Natives list and is performance related, use `[]` over `Array`.

Should you need to tell the future, a pre-defined length, use `Array`.

```javascript
var example = ['one', 'two'];

console.log(example[0]);
```

Prefer native methods over complicated code. Such as `.push`, `.pop`, `.splice`, `.sort`, `.filter`, `.map` (where available; **node.js**), and `.slice`.

### Cloning

Use `.slice` over iteration.

## Strings

Use `''` or `""` dependant on situation, just attempt to be consistent.

1. As a rule of thumb, generally I tend to use `""` when I know it may be long bodies of text or  is some sort of free-form string without regulations. Because it can contain `'` more likely than `"`.

```javascript
var slug = 'joe_biden'; // Slugs are restrictive, personally to be consistent, here I would use double quotes. It's just an example and you can still easily read / change it.
var name = "Joe Biden"; // Names can contain '
var biography = "Wouldn't it make more sense to be logical, and rational rather than precise and perfect? Nothing is perfect. I make mistakes, I'm human. I am Joe Biden.";
```

### Multiline

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

## Variables

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

### Other Styles

The first, commonly used, tends to be hard to read and scan when you view it inside of code contextually; Without context it looks alright. The gap between the line-numbers, and the variable can cause visual problems for scanning when code comes immediately after starting on the same vertical rhythm that `var` is on. Nesting and heirarchy get lost.

```javascript
// Single var statement, multiple variables, comma after, columnized.
// Loss of vertical rhythm.

var one = 1,
    two = 2,
    three = 3,
    four, 
    five, 
    six;
```

The next example, more commonly used in two-space code, while being cleaner and slightly easier to read provides new problems. Linting, and older engines may insert semicolons or check for trailing commas, which will throw errors here. Not only that, you still lose your vertical rhythm when viewing this block inside of code contextually.

I myself enjoyed this block for a year or two, now I avoid it like the plague.

```javascript
// Single var statement, multiple variables, comma before.
// Can cause problems in some situations.
// Loss of vertical rhythm.

var one = 1
  , two = 2
  , three = 3
  , four
  , five
  , six;
```

There is also the single line, this is just hard to read after a certain point so I will skip it. 
Nobody really uses it, if used, should only be for short un-assigned lists.

## Todo

Things I have not glossed over, yet here are some quick snippets of information you may find useful right away.

1. **Naming conventions.** (Personally `+1` for snake, camel, and pascal, also going over leading `$` vs `_` and when to use them.)
2. **Private variables.** (Personally prefer **real** private variables over cheap hacks such as leading underscore.)
3. **Casting and Coercion.** (It's pretty cool, fun, and many people don't know it exists.)
4. **Comments**. (Personal Findings: Doc-blocks are cool for generation, single line are great for annotation, amazing code doesn't need much inline comments.)
5. **Blocks** (Don't create variables inside blocks as a general rule of thumb, unless performance. Generally, using braces _multi-line_ style is easier to read. Sometimes it's acceptable to ignore them.)
6. **Functions** (When to var, when not to var. Always name them for logging sake.)
8. **Engines / Compilers** (There are many different ones, v8, rhino, etc.. They don't always interpret the same.)
9. **Semicolons** (What is ASI? How can you avoid it? What are some things you should do (use semicolons! memorize ASI rules if you don't!)
