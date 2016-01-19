# Webpack

Previously, we saw how PostCSS plugins can affect the processing of
CSS. To apply PostCSS, we need to use a build step. This is similar to
the build step one would use with SASS or LESS. Webpack will be our
build system of choice for this book.

> webpack takes modules with dependencies and generates static assets
> representing those modules.

Understanding webpack intimately is not going to be necessary for this
book. We will set up a project in this chapter (TODO: more here)...

To use webpack, we will need to teach webpack to process `.css`
files using [loaders][loaders]. Loaders are applied to the set of
files in your project, filtered by a regex. For example, in the code
below, we apply a series of loaders to all files which have been
required that end in `.css`.

```javascript
module.exports = {
  module: {
    loaders: [{
      test:   /\.css$/,
      loaders: ['style-loader', 'css-loader', 'postcss-loader']
    }]
  }
}
```

The `loaders` key indicates which processing steps will take place for
each `.css` file. They are evaluated from right to left, so first
`postcss-loader` is applied, then `css-loader` and finally
`style-loader`.

[loaders]: https://webpack.github.io/docs/loaders.html
