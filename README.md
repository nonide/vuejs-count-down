# vuejs-count-down

> Vue.js countdown component

<p align="center">
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square" alt="Software License" />
  </a>
  <a href="https://npmjs.org/package/vuejs-count-down">
    <img src="https://img.shields.io/npm/v/vuejs-count-down.svg?style=flat-square" alt="Packagist" />
  </a>
  <a href="https://github.com/nonide/vuejs-count-down/issues">
    <img src="https://img.shields.io/github/issues/nonide/vuejs-count-down.svg?style=flat-square" alt="Issues" />
  </a>
</p>

## Getting started

### Installation
```
npm install --save vuejs-count-down
```

### Usage

- CommonJS: `var CountDown = require('vuejs-count-down')`
- ES2015: `import CountDown from 'vuejs-count-down'`


```js
components: {
    CountDown,
},
methods: {
    countDownProgress(time) {
        this.countDownSeconds = time
    },
    countDownFinished() {
        // restart when countdown ends
        this.$refs.countdown.$emit('restart')            
    }
}
```

```html
<CountDown
    ref="countdown"
    :time="30"
    @onProgress="countDownProgress"
    @onFinish="countDownFinished"
>
    Time Remaining: {{countDownSeconds}} seconds.
</CountDown>
<!-- Time Remaining：30 seconds -->
```

## Props

### time

- Type: `Number`
- Required

Total number of time in seconds for the countdown.

### autoStart

- Type: `Boolean`
- Default: `true`

Start countdown automatically when the component is created.


## Methods

### start

Start the countdown.

### stop

Stop the countdown.

### restart

Init the countdown and start again.


## Events

### onProgress

This event fires in progress (each second)

### onFinish

This event fires when countdown ends.


## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email . instead of using the issue tracker.

## Credits

- [Pablo Hernández Nonide][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[link-author]: https://github.com/nonide
[link-contributors]: ../../contributors
