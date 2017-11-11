---
title: "Installation & Usage"
anchor: "usage"
weight: -1
---

Integrating Rucksack into your workflow is easy. It's built on [PostCSS](https://github.com/postcss/postcss), which provides plugins for most build tools. You can also compile CSS directly on the command line, or with the JavaScript API.

<div style="overflow: auto;">

{{% usage title="With Gulp" id="gulp" img="https://www.rucksackcss.org/img/usage/gulp.png" %}}

Use [gulp-postcss](https://github.com/postcss/gulp-postcss)

```js
const gulp = require('gulp');
const postcss = require('gulp-postcss');
const rucksack = require('rucksack-css');

gulp.task('rucksack', () => {
  return gulp.src('src/*.css')
    .pipe(postcss([ rucksack() ]))
    .pipe(gulp.dest('dist'));
});
```

{{% /usage %}}

{{% usage title="With Grunt" id="grunt" img="https://www.rucksackcss.org/img/usage/grunt.png" %}}

Use [grunt-postcss](https://github.com/nDmitry/grunt-postcss)

```js
grunt.initConfig({
  postcss: {
    options: {
      processors: [
        require('rucksack-css')()
      ]
    },
    dist: {
      src: 'css/*.css'
    }
  }
});
```

{{% /usage %}}

{{% usage title="Command Line" id="cli" img="https://www.rucksackcss.org/img/usage/cli.png" %}}

Use Rucksack on the command line with [postcss-cli](https://github.com/postcss/postcss-cli)

```sh
$ npm i postcss-cli -g
```

`postcss.config.js`

```js
module.exports = {
  use: [ 'rucksack-css' ]
};
```

```sh
$ postcss "input.css" -o 'output.css'
```

{{% /usage %}}

{{% usage title="Javascript API" id="postcss" img="https://www.rucksackcss.org/img/usage/postcss.png" %}}

Since Rucksack is just a PostCSS plugin, you can also use it in JS/Node directly, via the PostCSS API

```js
const postcss = require('postcss');
const rucksack = require('rucksack-css');

postcss([ rucksack() ])
  .process(css, { from: 'src/style.css', to: 'style.css' })
  .then(result => {
      fs.writeFileSync('style.css', result.css);
      if ( result.map ) fs.writeFileSync('style.css.map', result.map);
  });
```

See the [PostCSS Docs](https://github.com/postcss/postcss) for examples for your environment.

{{% /usage %}}

{{% usage title="With Stylus" id="stylus" img="https://www.rucksackcss.org/img/usage/stylus.png" %}}

Rucksack can be used as a Stylus plugin with [PostStylus](https://github.com/seaneking/poststylus)

```js
stylus(css).use(poststylus('rucksack-css'))
```

See the [PostStylus Docs](https://github.com/seaneking/poststylus) for more examples for your environment.
{{% /usage %}}

</div>
