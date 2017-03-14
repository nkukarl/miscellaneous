```html
<div>
    A bunch of words you see
<div>
```

Notice in the html code above, there are actually
two line breaks, one before the line of text and
one after, which allow the text to be on its own
line.
When the text renders in the browser, those line
breaks appear as if they are stripped out.
Also stripped out are the extra spaces on the line
before the first letter.
If we want to force the browser to display those
line breaks and extra white space characters,
we can use `white-space:pre;`

It is called `pre` because the behaviour is that
as if you had wrapped the text in `<pre></pre>`
tags.
