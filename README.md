# hugo-static-tweet-demo

Demo site

https://gohugo.io/getting-started/quick-start/

```
hugo new site quickstart
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke
git submodule add https://github.com/ianmuchina/hugo-static-tweet.git themes/hugo-static-tweet
echo "theme = ['hugo-static-tweet', 'ananke']" >> config.toml
hugo server
```

The important files:

`config.toml` adds the theme component and the actual theme.

```toml
# config.toml
theme = ['hugo-static-tweet', 'ananke']
```

`assets/hugo-tweet/_overrides.scss` explicitly sets a font family and sets the tweet color theme
to just light. 

```scss
// assets/hugo-tweet/_overrides.scss
.tweet {
    @extend .light;
    font-family: sans-serif;
}
```

## Deployment

Most hosting providers (ie: vercel) does not automatically use the latest hugo version. Use the following commands to succesfully build this site on any environment.

### Install Command

Adds an empty package.json & installs the latest [`hugo-extended`](https://www.npmjs.com/package/hugo-extended) package from npm.

```bash
# Install dependencies
npm init -y && pnpm add hugo-extended
```

## Build command
This runs the `hugo-extended` package. Output is still the `public` folder.

```bash
# build the site
pnpm exec hugo-extended
```
