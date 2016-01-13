#My Code Style Guide

https://google.github.io/styleguide/htmlcssguide.xml

##The doctype

```html
<!doctype html>
```

Lowercase is better for gzip. Weird, but true. Only XHTML5 requires an uppercase DOCTYPE.

##Lang

```html
<html lang="en-us">
```

Again, lowercase is better for gzip. Language codes are specced to be case-insensitive, the normal casing schema (`en-Brail-US`) is just convention.

The assumed default is `lang="en-US"` but an explicit declaration is necessary for CSS typographic niceties.

##Charset

```html
<meta charset="utf-8">
```

Use `utf-8`, not `utf8`. The latter is nonstandard and has known browser bugs (IE10-).

Use `meta[charset]` and not `http-equiv="Content-Type"`. The latter has problems according to the HTML5 spec, and is longer anyway.

Don't include both.

Make sure this happens within the first 1024 bytes of an HTML file to avoid XSS & browser slowdowns. IE in particular has blogged about this "restarting." This is probably the best reason to avoid the multiple `<html>` start tags braced with conditional comments. Excessive classes on the root element are also a problem and have some performance issues as well.

Always use UTF-8. There are no reasons not to, anymore.

##X-UA-Compatible

```html
<meta http-equiv="x-ua-compatible" content="ie=edge">
```

Lowercase for gzip.

Try not to use this, and instead use the real HTTP header. There's known problems with the `<meta>` version, and it can be trigger parsing "restarts" much like the charset declaration.

Always use `ie=edge`.

`chrome=1` is so outdated it's not even funny anymore. Remove.

##`<title>`

Structure like "Document Title | Site Name".

##Viewport

Always use this one:

```html
<meta name="viewport" content="width=device-width,height=device-height,initial-scale=1,minimum-scale=1,shrink-to-fit=no">
```

http://codepen.io/write/meta-name-viewport-reloaded
https://developer.apple.com/library/prerelease/mac/releasenotes/General/WhatsNewInSafari/Articles/Safari_9_1.html#//apple_ref/doc/uid/TP40014305-CH10-SW6

## URLs

Use root-relative URLs where possible.

* `/root/relative`
* `./directory/relative` - Use this syntax instead of the "empty" directory-relative prefix.

Use of the parent directory syntax is discouraged, because it easily results in 404s and infinite linkchains.

Except for `<link rel="canonical">`; that one should be fully-qualified, including protocol. (Google *does* consider `https:` and `http:` to be separate sites, since they technically are.)

Instead of using protocol-relative URLs, specify `https:` by default.
