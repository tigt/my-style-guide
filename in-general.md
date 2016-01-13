# In General

## UTF-8 everywhere

[Why?](http://utf8everywhere.org/)

It's `utf-8`, not `utf8`. Technically it's supposed to be uppercase, but nothing seems to care.

Any kind of XML is assumed by default to be UTF-8. You don't need to specify it in the initial processing instruction.

Avoid the Byte-Order Mark; it works great in browsers, breaks lots of things on the back-end. Including the user's back-end, if they try processing with it.
