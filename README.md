# Markdown styles for IBM Carbon Design System

The IBM Carbon Design System css resets HTML elements like `<p>` and `<h1>` which leads to flat-looking html when rednering markdown.

## How it works
Based heavily on [GitHub markdown css](https://github.com/sindresorhus/github-markdown-css), this package re-styles html elements under css class `markdown-body`.
1. Start with GitHub css in [GitHub markdown css](https://github.com/sindresorhus/github-markdown-css)
2. Selectively bring-in styles from Carbon. For example:
    ```scss
    .markdown-body h5 {
      @include carbon--type-style('expressive-heading-01');
    }

    .markdown-body ul {
      @extend .bx--list--unordered;
    }

    ```
    
## Usage
```sh
npm install carbon-markdown-scss
```

```javascript
import React from 'react';
import marked from 'marked';
import 'carbon-markdown-scss/scss/github-carbon.scss';

export default ({markdown}) => {
  let markdownHtml = marked(markdown);

  return (
    <div
      className="markdown-body"
      dangerouslySetInnerHTML={{__html: markdownHtml}}
    />
  );
};
```
