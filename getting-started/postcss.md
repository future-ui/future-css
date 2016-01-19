# PostCSS

PostCSS is the next generation of CSS processors. Past generations of
which included LESS, Stylus and SASS. PostCSS's main differentiator is
it's modular nature. The Abstract Syntax Tree (AST from now on) is
trivial to access and modify with
[plugins](https://github.com/postcss/postcss/blob/master/docs/writing-a-plugin.md). You
can see an example of this by exploring
[the AST](http://astexplorer.net/#/np0DfVT78g/1) in a browser.

Day to Day, you do not have to play with the AST. The main takeaway
from knowing how easy it is to manipulate the CSS AST in a structured
way is the power that plugins have. The PostCSS ecosystem has plugins
which can introduce new CSS syntax, provide fallbacks and rewrite all
of the urls in a set of stylesheets. As a user of these plugins, the
reader will benefit from plugin authors having access to the full
power of JavaScript to manipulate the AST of their CSS.

## Example

So what does using PostCSS look like? The following example uses a set
of PostCSS plugins (contained in [cssnext](http://cssnext.io/)) to
enable functionality such as custom properties, var() and reduced calc
statements.

```css
:root {
  --fontSize: 1rem;
  --mainColor: #12345678;
}

body {
  color: var(--mainColor);

  font-size: var(--fontSize);
  line-height: calc(var(--fontSize) * 1.5);
  padding: calc((var(--fontSize) / 2) + 1px);
}
```

This compiles to the following final stylesheet.

```css
body {
  color: #123456;
  color: rgba(18, 52, 86, 0.47059);

  font-size: 16px;
  font-size: 1rem;
  line-height: 24px;
  line-height: 1.5rem;
  padding: calc(0.5rem + 1px);
}
```

There are a few interesting results to note:

* calc statements were reduced as far as possible. Down to a constant
  in the case of `line-height`.
* A set of variables was declared, used in calculations, and removed
  in the final stylesheet.
* A fallback for each `rem` value was declared automatically in
  pixels.
