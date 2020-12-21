# Coding Guideline: HTML

## Doctype and metadata

### Doctype

You should use the HTML5 doctype. It is short, easy to remember, and backwards
compatible:

```
<!DOCTYPE html>
```

### Document language

Set the document language using the lang attribute on your `<html>` element:

```
<html lang="en-US">
```

This is good for accessibility and search engines, helps with localizing content,
and reminds people to use best practices.

### Document characterset

You should also define your document's characterset like so:

```
<meta charset="utf-8">
```

Use UTF-8 unless you have a very good reason not to; it will cover your character
needs pretty much regardless of what language you are using in your document. In
addition, you should always specify the characterset as early as possible within
your HTML's `<head>` block (within the first kilobyte), as it protects against a
rather nasty Internet Explorer security vulnerability.

### Viewport meta tag

Finally, you should always add the viewport meta tag into your HTML `<head>`, to give the example a better chance of working on mobile devices. You should include at least the following in your document, which can be modified later on as the need arises:

```
<meta name="viewport" content="width=device-width">
```

## General markup coding style

### Use lowercase

Use lowercase for all element names and attribute names/values, as it looks
neater and means you can write markup faster:

This is good:

```
<p class="nice">This looks nice and neat</p>
```

This is not so good:

```
<P CLASS="WHOA-THERE">Why is my markup shouting?</P>
```

### Trailing slashes

Don't include XHTML-style trailing slashes for empty elements, as they are
unnecessary and slow things down. They can also break old browsers if you are not
careful (although from what we can recall, this hasn't been a problem since
Netscape 4).

This is fine:

```
<input type="text">
<hr>
```

The slashes are not needed:

```
<input type="text" />
<hr />
```

### Quoting attributes

You should put all attribute values in double quotes. It is tempting to omit
quotes since HTML5 allows this, but markup is neater and easier to read if you do
include them. For example, this is better:

```
<img src="images/logo.jpg" alt="A circular globe icon" class="no-border">
```

than this:

```
<img src=images/logo.jpg alt=A circular globe icon class=no-border>
```

It can also cause problems — in the above example the alt attribute will be
interpreted as multiple attributes, because there are no quotes to specify that
"A circular globe icon" is a single attribute value.

### Use double quotes

Use double quotes for HTML, not single quotes:

Good:

```
<p class="important">Yes</p>
```

Bad:

```
<p class='important'>Nope</p>
```

### Boolean attributes

Don't write out boolean attributes in full; you can just write the attribute name
to set it. For example, you can write:

```
<input type="text" required>
```

This is perfectly understandable and works fine. Instead of writing out the
longer version with the value

```
<input type="text" required="required">
```

Which is supported but not necessary.

### Class and ID names

Use semantic class/ID names, and separate multiple words with hyphens. Don't use
camelCase.

Good:

```
<p class="editorial-summary">Blah blah blah</p>
```

Bad:

```
<p class="bigRedBox">Blah blah blah</p>
```

### Entity references

Don’t use entity references unnecessarily — use the literal character wherever
possible (you'll still need to escape characters like angle brackets and quote
marks).

As an example you could just write

```
<p>© 2018 Me</p>
```

Instead of

```
<p>&copy; 2018 Me</p>
```

This is fine as long as you declare a UTF-8 character set.

