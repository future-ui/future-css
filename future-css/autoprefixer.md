# Autoprefixer

As browsers implement new specs, they often add vendor-specific
prefixes to namespace features. Flexbox is one example of this:

```css
.page-wrap {
    display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6, BB7 */
    display: -ms-flexbox;  /* TWEENER - IE 10 */
    display: -webkit-flex; /* NEW - Safari 6.1+. iOS 7.1+, BB10 */
    display: flex;         /* NEW, Spec - Firefox, Chrome, Opera */
}

.main-nav,
.main-sidebar {
    -webkit-box-flex: 1;   /* OLD - iOS 6-, Safari 3.1-6 */
    width: 20%;            /* For old syntax, otherwise collapses. */
    -webkit-flex: 1;       /* Safari 6.1+. iOS 7.1+, BB10 */
    -ms-flex: 1;           /* IE 10 */
    flex: 1;               /* NEW, Spec - Firefox, Chrome, Opera */
}
```

When really all we wanted to write was:

```css
.page-wrap {
    display: flex;
}

.main-nav,
.main-sidebar {
    flex: 1;
}
```

Autoprefixer brings this closer to a reality. The original code
snippet here supports a lot more of the (old/tweener/etc) syntax than
we needed to and remembering all of the prefixes (and
[hacks](https://github.com/postcss/autoprefixer/tree/master/lib/hacks))
for every vendor across all properties is a rough proposition.

## Supported Prefixes

[](https://github.com/postcss/autoprefixer/wiki/support-list)

## Old Prefixes

Prefixes in your CSS which are no longer necessary will get removed by
Autoprefixer.

```css
a {
    -webkit-border-radius: 5px;
    border-radius: 5px;
}
```

compiles to:

```css
a {
    border-radius: 5px;
}
```

## Picking a Browser Range

https://github.com/ai/browserslist
