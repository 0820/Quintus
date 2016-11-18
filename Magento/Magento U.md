##Layout
There are __layouts__ and __page layouts__

Magento 2 has two rendering systems:

1. one is similar to Magento 1

2. the new one is based on page objeects. There are **two** rendering layouts: `View::loadLayout()` and `View::renderLayout()`

##Theme
Add theme yo grunt configuration
```js
module.exports = {
  <theme>: {
    area:'frontend',
    name: '<Vendor>/<theme>',
    locale: '<language>',
    files: [
      '<path_to_file1>', // path to root source file
      '<path_to_file2>'
    ],
  dsl: 'less'
  },
```
