# Chart.js Error Bars Plugin
[![datavisyn][datavisyn-image]][datavisyn-url] [![NPM Package][npm-image]][npm-url] [![CircleCI][circleci-image]][circleci-url]

[Chart.js](http://www.chartjs.org/) plugin for adding error bars to Line-, Barcharts or hierarchical Barcharts. This plugin also works with the [Hierarchical Scale Plugin](https://github.com/datavisyn/chartjs-scale-hierarchical).

Try the demo on [Codepen](https://codepen.io/sluger/pen/YjJKYy).

![selection_037](https://user-images.githubusercontent.com/5220584/43774415-4ab5ae88-9a49-11e8-813d-48d607d45225.png)
![selection_038](https://user-images.githubusercontent.com/5220584/43774418-4d08132e-9a49-11e8-9e90-723ef91783c7.png)
![selection_039](https://user-images.githubusercontent.com/5220584/43774420-4e7d7546-9a49-11e8-8cc9-67c63de96081.png)

## Install
```bash
npm install --save chart.js chartjs-plugin-error-bars
```

## Usage
Datasets must define an `errorBars` object that contains the error bar property key (same as in the used scale) and values `plus` and `minus`. Plus values are always positive, and minus vice versa.

*Categorical scale usage:*
```javascript
  data: {
    labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
    datasets: [{
      ...
      errorBars: {
        'February': {plus: 15, minus: -34},
        'March': {plus: 5, minus: -24},
        'May': {plus: 35, minus: -14},
        'June': {plus: 45, minus: -4}
      }, ...
```

*Hierarchical scale plugin usage:*
```javascript
  data: {
    labels: [
      'A',
      {
        label: 'C1',
        children: ['C1.1', 'C1.2', 'C1.3', 'C1.4']
      }
    ],
    datasets: [{
      ...
      errorBars: {
        'A': {plus: 25, minus: -10},
        'C1.2': {plus: 14, minus: -15},
        'C1': {plus: 34, minus: -5}
      }, ...
  }
```

Find more [Samples](https://github.com/datavisyn/chartjs-plugin-error-bars/tree/master/samples) on Github.


## Options
```javascript
  options: {
    ...

    plugins: {
      chartJsPluginErrorBars: {
        /**
         * stroke color
         * @default: derived from borderColor
         */
        color: '#666',

        /**
         * bar width in pixel as number or string or bar width in percent based on the barchart bars width (max 100%)
         * @default 10
         */
        width: 10 | '10px' | '60%',
        
        /**
         * lineWidth as number, or as string with pixel (px) ending
         */
        lineWidth: 2 | '2px',

        /**
         * whether to interpet the plus/minus values, relative to the value itself (default) or absolute
         * @default false
         */
        absoluteValues: false
      }
    }

  ...
}
```


## Building

```sh
npm install
npm run build
```


***

<div style="display:flex;align-items:center">
  <a href="http://datavisyn.io"><img src="https://user-images.githubusercontent.com/1711080/37700685-bcbb18c6-2cec-11e8-9b6f-f49c9ef6c167.png" align="left" width="50px" hspace="10" vspace="6"></a>
  Developed by &nbsp;<strong><a href="http://datavisyn.io">datavisyn</a></strong>.
</div>

[datavisyn-image]: https://img.shields.io/badge/datavisyn-io-black.svg
[datavisyn-url]: http://datavisyn.io
[npm-image]: https://badge.fury.io/js/chartjs-plugin-error-bars.svg
[npm-url]: https://npmjs.org/package/chartjs-plugin-error-bars
[circleci-image]: https://circleci.com/gh/datavisyn/chartjs-plugin-error-bars.svg?style=shield
[circleci-url]: https://circleci.com/gh/datavisyn/chartjs-plugin-error-bars
