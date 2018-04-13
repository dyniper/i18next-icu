# Introduction

[![Travis](https://img.shields.io/travis/i18next/i18next-icu/master.svg?style=flat-square)](https://travis-ci.org/i18next/i18next-icu)
[![Coveralls](https://img.shields.io/coveralls/i18next/i18next-icu/master.svg?style=flat-square)](https://coveralls.io/github/i18next/i18next-icu)
[![npm version](https://img.shields.io/npm/v/i18next-icu.svg?style=flat-square)](https://www.npmjs.com/package/i18next-icu)
[![David](https://img.shields.io/david/i18next/i18next-icu.svg?style=flat-square)](https://david-dm.org/i18next/i18next-icu)

This changes i18n format from i18next json to ICU using [yahoo/intl-messageformat](https://github.com/yahoo/intl-messageformat)

# Getting started

Source can be loaded via [npm](https://www.npmjs.com/package/i18next-icu) or [downloaded](https://github.com/i18next/i18next-icu/blob/master/i18nextICU.min.js) from this repo.

```
# npm package
$ npm install i18next-icu
```

Wiring up:

```js
import i18next from 'i18next';
import ICU from 'i18next-icu';

i18next
  .use(ICU)
  .init(i18nextOptions);
```

- As with all modules you can either pass the constructor function (class) to the i18next.use or a concrete instance.
- If you don't use a module loader it will be added to `window.i18nextICU`

## Backend Options

```js
{
  // per default icu functions are parsed once and cached for subsequent calls
  memoize: true
}
```

Options can be passed in by setting options.i18nFormat in i18next.init:

```js
import i18next from 'i18next';
import ICU from 'i18next-icu';

i18next
  .use(ICU)
  .init({
    i18nFormat: options
  });
```

### more complete sample

```js
import i18next from 'i18next';
import ICU from 'i18next-icu';

i18next
  .use(ICU)
  .init({
    lng: 'en',
    resources: {
      en: {
        translation: {
          'key': 'You have {numPhotos, plural, ' +
            '=0 {no photos.}' +
            '=1 {one photo.}' +
            'other {# photos.}}'
        }
      }
    }
  });

 i18next.t('key', { numPhotos: 1000 }); // -> You have 1,000 photos.
```
