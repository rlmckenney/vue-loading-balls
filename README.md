# Vue Loading Balls

A bouncing balls loading animation component for Vue.js 2.x that uses smooth SGV animation for natural looking motion.

Inspired by Nash Vail's article, [How you can use simple trigonometry to create better loaders](https://www.codementor.io/nashvail/how-you-can-use-simple-trigonometry-to-create-better-loaders-jntt54acz).

And, Sarah Drasner's book on [SVG Animations](http://shop.oreilly.com/product/0636920045335.do) in which she reminds us that animation aids in perceived performance.

> Humans over-estimate passive waits by 36%
>
> -- _Richard Larson of MIT_

## Compatibility

Vue.js 2.x

## Installation

```bash
$ npm install vue-loading-balls --save
```

or

```bash
$ yarn add vue-loading-balls
```

## Usage

Import the LoadingBalls component in the script section of your app ...

```js
import LoadingBalls from 'vue-loading-balls'

export default {
  components: { LoadingBalls },
  data: () => ({
    isLoading: true
  })
  // ...
}
```

In the template section, simply drop in the component element `<loading-balls />`. Of course you will want to conditionally display it based on some state property like `isLoading` from the example above.

```html
<template>
  <loading-balls v-if="isLoading" />
  <main v-else>
    <h1>Main content here ...</h1>
  </main>
</template>
```

You should now see ...

![three black balls bouncing vertically](https://github.com/rlmckenney/vue-loading-balls/raw/master/public/loading-balls-3-black.gif)

### Example with options

```html
<template>
  <loading-balls
    v-if="isLoading"
    :count="4"
    :radius="8"
    color="#4b0082"
  />
  <main v-else>
    <h1>Main content here ...</h1>
  </main>
</template>
```

Now you should see ...

![five purple balls bouncing vertically](https://github.com/rlmckenney/vue-loading-balls/raw/master/public/loading-balls-5-purple.gif)

## Configurable options:

| Key    | Description                                                           | Default | Value            |
| ------ | --------------------------------------------------------------------- | ------- | ---------------- |
| count  | number of balls                                                       | 3       | Number \| String |
| color  | colour of the balls -- any valid CSS color value (_hex, rgb, or hsl_) | #333333 | String           |
| radius | radius of the balls in px                                             | 10      | Number \| String |
| width  | width in px of the enclosing SVG element                              | 300     | Number \| String |
| height | height in px of the enclosing SVG element                             | 300     | Number \| String |

Step timing and amplitude are automatically calculated to ensure smooth, natural looking animation.

## Versioning

We use [SemVer](https://semver.org) for versioning. For the versions available, see the [tags on this repository](https://github.com/rlmckenney/vue-loading-balls/tags).

## License

This project is licensed under the MIT License - see the [LICENSE.md](https://github.com/rlmckenney/vue-loading-balls/blob/master/LICENSE.md) file for details
