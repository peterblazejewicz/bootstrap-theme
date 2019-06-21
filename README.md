# Bootstrap Theme setup

Bootstrap 4 custom theme setup - if you want to create your own builds.

## Tools

The same tools as in BS tool-chain required to built CSS theme with following changes:

1) `sass-lint` Ruby bundle replaced with drop-in NPM replacement `scss-lint`
1) `node-sass` importer added to use short notation based on NPM packages:

```scss
@import '~bootstrap/scss/functions';
@import '~bootstrap/scss/variables';
@import '~bootstrap/scss/mixins';
@import '~bootstrap/scss/print';
```

## Usage

```bash
npm run css

> bootstrap-theme@1.0.0 css /Users/piotrblazejewicz/git/bootstrap-theme
> npm-run-all css-lint css-compile css-prefix css-minify


> bootstrap-theme@1.0.0 css-lint /Users/piotrblazejewicz/git/bootstrap-theme
> sass-lint --config .scss-lint.yml scss/*.scss


> bootstrap-theme@1.0.0 css-compile /Users/piotrblazejewicz/git/bootstrap-theme
> node-sass --importer node_modules/node-sass-package-importer/dist/cli.js --output-style expanded --source-map true --source-map-contents true --precision 6 scss/bootstrap-theme.scss dist/css/bootstrap-theme.css

Rendering Complete, saving .css file...
Wrote Source Map to /Users/piotrblazejewicz/git/bootstrap-theme/dist/css/bootstrap-theme.css.map
Wrote CSS to /Users/piotrblazejewicz/git/bootstrap-theme/dist/css/bootstrap-theme.css

> bootstrap-theme@1.0.0 css-prefix /Users/piotrblazejewicz/git/bootstrap-theme
> postcss --config build/postcss.config.js --replace dist/css/*.css

✔ Finished dist/css/bootstrap-theme.css (184ms)
✔ Finished dist/css/bootstrap-theme.min.css (177ms)

> bootstrap-theme@1.0.0 css-minify /Users/piotrblazejewicz/git/bootstrap-theme
> cleancss --level 1 --source-map --source-map-inline-sources --output dist/css/bootstrap-theme.min.css dist/css/bootstrap-theme.css
```

## Author

@peterblazejewicz
