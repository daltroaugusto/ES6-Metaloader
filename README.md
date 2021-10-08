# ES6-Metaloader
Simple tiny ES6 async function to dynamically generate title and metatags, making your website more organized and simplifying build of (almost) library-less projects.

# Usage
## Basic usage
```javascript
import Metaloader from 'assets/metaloader.min.js';

// function is sync (doesn't use any await symbol) if we pass a object directly
Metaloader({
  title: "some title",
  description: "some description",
  charset: "utf-8",
  viewport: "width=device-width, initial-scale=1",
  keywords: "really,true,words,here",
  robots: "nofollow,noindex",
  author: "Daltro Augusto",
  creator: "Daltro Augusto",
  canonical: "https://foo.com",
  locale: "pt_BR",
  type: "article",
  image: "https://foo.com/image.png",
  url: "https://foo.com/this-article",
  site_name: "Foo",
});
```

## Async context and an external JSON object
```javascript
async () => {
  const response = await fetch("something.txt");
  const thistext = await response.text();
  document.querySelector('span').innerHTML = thistext;

  await Metaloader({
    jsonSource: "./assets/MyMetaValuesObject.json"
  });
  // will wait fetching and loading JSON object then we'll be able to...
  window.alert(document.querySelector('title').innerHTML);
};
```
