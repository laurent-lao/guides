# Using Raw Redirects

In `index.html`

```html
remoteMarkdown: {
  tag: 'CustomTag',
},
```

In `_raw-redirect/custom`

```markdown
<!-- markdownlint-disable -->
[customTag](link)
```

Then link to the `_raw-redirect/custom` page from a document

# Lists

* [raw-redirect](https://raw.githubusercontent.com/laurentlaurent/qmk_firmware/master/keyboards/preonic/keymaps/laurentlaurent/readme.md)