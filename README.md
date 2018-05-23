# Vue Loading Balls

## Bouncing balls loading component for Vue.js with smooth SGV animation

Inspired by Nash Vail's article, [How you can use simple trigonometry to create better loaders](https://www.codementor.io/nashvail/how-you-can-use-simple-trigonometry-to-create-better-loaders-jntt54acz).

And, Sarah Drasner's book on [SVG Animations](http://shop.oreilly.com/product/0636920045335.do) in which she reminds us that animation aids in perceived performance.

> Humans over-estimate passive waits by 36%
>
> -- _Richard Larson of MIT_

## Browser Support

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

-- insert gif here --

### Example with options

```html
<template>
  <loading-balls
    v-if="isLoading"
    :count="4"
    :radius="8"
    :color="#4b0082"
  />
  <main v-else>
    <h1>Main content here ...</h1>
  </main>
</template>
```

Now you should see ...

-- insert gif here --

## Configurable options:

| Key    | Description                               | Default | Value                                                   |
| ------ | ----------------------------------------- | ------- | ------------------------------------------------------- |
| count  | number of balls                           | 3       | Number                                                  |
| color  | colour of the balls                       | #333333 | String (_Any valid CSS color value - hex, rgb, or hsl_) |
| radius | radius of the balls in px                 | 10      | Number                                                  |
| width  | width in px of the enclosing SVG element  | 300     | Number                                                  |
| height | height in px of the enclosing SVG element | 300     | Number                                                  |

Step timing and amplitude are automatically calculated to ensure smooth, natural looking animation.
