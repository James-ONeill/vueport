# VuePort

Vueport is a set of Vue JS data provider components designed to make it easy
to add scroll effects to your Vue application.

## Getting started

To add VuePort to your app simply run `npm install vueport`. Once installed it
exposes two components that you can import.

```javascript
import {
    VueportPageScroll,
    VueportElementPosition
} from "vueport";
```

## Using `VueportPageScroll`

The `VueportPageScroll` component uses scoped slots to provide the current
scroll position to your components. It can be used to build page progress
indicators, animations that depend on the overall scroll position, etc.

```
<vueport-page-scroll>
    <div slot-scope="scrollPosition">
        ...
    </div>
</vueport-page-scroll>
```

### Exposed values

`VueportPageScroll` makes the following values available to you:

- `scrollY` The current value of `window.scrollY`
- `scrollHeight` The current value of `window.documentElement.scrollHeight`
- `clientHeight` The current value of `window.documentElement.clientHeight`
- `scrollableHeight` The height of the scrollable area of the document.
- `scrollPcnt` The current percentage of the page that has been scrolled.

## Using `VueportElementPosition`

The `VueportElementPosition` component uses scoped slots to provide the current
position of the component it wraps relative to the device viewport.


```
<vueport-element-position>
    <div slot-scope="elementPosition">
        ...
    </div>
</vueport-element-position>
```

### Exposed values

`VueportElementPosition` makes the following values available to you:

- `boundingClientRect` The current `BoundingClientRect` for the component
- `visible` Boolean. Whether the component is currently visible on the viewport
- `fullyVisible` Boolean. Whether the component is currently fully visible on the viewport
- `shown` Boolean. Whether the component has been shown. This is set to `true`
when then `visible` first becomes `true` and remains so for the rest of the
component lifecycle
- `topPcnt` The position of the top of the element relative to the top of the
viewport as a percentage
- `bottomPcnt` The position of the bottom of the element relative to the top of the
viewport as a percentage
- `center` The vertical position of the center of the element in pixels
- `centerPcnt` The position of the center of the element relative to the top of the viewport as a percentage

## Coming Soon

VuePort is still a work in progress and is being added to all the time there
will be more features added to both components and more components added in the
near future. I will also be working on improving the documentation including
a demo site built using VuePort and some examples of how to build cool scrolling
animations using VuePort.

## About the Author

Hi, I'm James O'Neill and I built VuePort. I'm a developer from Bristol, England.

If you want to know more about me you can check out my [personal site](https://jamesoneill.eu) or follow me on Twitter [@jamesoneill83](https://twitter.com/jamesoneill83).







