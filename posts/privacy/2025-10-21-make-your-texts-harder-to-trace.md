---
title: "Make Your Texts Harder To Trace"
date: 2025-10-21
author: "Chris Bradley"
tags: [obfuscate, cyrillic, homoglyph, unicode, glpyhshift, text]
description: "Make your texts harder to trace with GlpyhShift"
readtime: "44sec"
---

# Make Your Texts Harder To Trace
So when someone tries to searches for your texts, it shows up, right? It's because you typed them in normal English like everyone else would. And that's what we're going to make it harder to trace. For example:

Normal text in Latin letters:
```
I love my government!
```

Obfuscated homoglyph text:
```
Ι lоvе mу ɡоvеrnmеnt!
``` 

> [!NOTE]
> Please be responsible, I am not encouraging any illegal activites but demonstrating how similar looking letters can be used to create hard-to-detect text variations

## Using Letters From Different Languages
A lot of letters from other languages are similar to English letters, like the following example.
|English|Cyrillic|Greek|Czech|
|-|-|-|-|
|A|А|Α
|B|В|Β
|C|С|
|D|||Ď|
|E|Е|Ε
[[source]](https://en.wikipedia.org/wiki/Wikipedia:Language_recognition_chart)

There is actually a lot more letters than you think, which will make the text harder to trace.

## GlyphShift
What if there was a tool to automatically change the given text and obfuscates them? That's why [GlyphShift](https://github.com/evenblad3/GlyphShift) exists! The tool automatically copies the given normal text into the one we want.
