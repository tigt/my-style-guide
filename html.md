# Personal Style Guide: HTML

## Syntax

```html
<div class="box important isolated">
  <img src="/img/example.png" alt="" />
</div>
```

Tag names and attributes are always lowercase, except for inline SVG, where they're camel-cased as the spec describes.

Self-closing tags are flagged with a closing ` />`, which is solely for human readability. [Those hypothetic mobile browsers that could only parse well-formed XML don't exist.](https://simon.html5.org/articles/mobile-results) [Browsers that choke on a trailing slash without a preceding space *aren't* fiction](link to StackOverflow answer about this here), so be careful!

A HTML minifier should remove them from the output. (Make sure it's smart enough to not do that for inline SVG & MathML!)

### Attributes

Attributes are always surrounded by double quotes. Internal quotes should always be Unicode curly ones, but if those are unsuitable, use `&quot;`. Stripping quotes is a job for a minifier, because the rules for omitting them are arcane and annoying.

## Boilerplate HTML

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Page | Site</title>
  </head>
  <body>

  </body>
</html>
```

The lowercase `<!doctype>` is better for gzip, which seems silly but affects the critical path enough that it's worth bothering.

## URLs

Prefer relative URLs, ideally from the site root (`href="/folder/path/file"`), but sometimes fully-qualified, protocol-relative, or current working directory-relative are a better choice. When using the current working directory, **never** use the bare beginning (`href="path/file"`), always prefix with `./` (`href="./path/file"`).

## Language codes

Language codes should always be lowercase for gzip purposes.

## OpenGraph, Twitter Cards, and other folderol

As silly as this stuff is, it's nice UX for many scrapers at this point. (Pinterest, Skype, Tumblr, Reddit, AppleBot...) Being a nice citizen with it is ideal.

### Twitter Cards

Image previews, whether uploaded or not, always come in 2:1 dimensions. Make sure nothing important gets cut off.

## Common HTML molecules

"Molecules" are larger, very common constructions from combining elements. (Get it?)

### Blockquotes

All `<blockquote>`s contain a `<p>`, even for just one line:

```html
<blockquote>
  <p>Text here...</p>
</blockquote>
```
