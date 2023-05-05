# hugo-static-tweet-demo

Example repo showcasing hugo tweet component.

## tldr

Copy paste this to make a quick example repo. 

Ensure you're using hugo extended and the version is `110` or later.

```bash
#!/bin/bash
# Create new site
hugo new site quickstart
cd quickstart
# initialize git repo
git init
# add anake theme
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke
# add static tweet theme
git submodule add https://github.com/ianmuchina/hugo-static-tweet.git themes/hugo-static-tweet
# add toml config
echo "theme = ['hugo-static-tweet', 'ananke']" >> config.toml
# add new draft post
hugo new posts/tweet.md
# add tweet to post
echo '{{<tweet id="20">}}' >> content/posts/tweet.md
# add css overrides to make it look nice
mkdir assets/hugo-tweet/ 
touch assets/hugo-tweet/_overrides.scss
echo ".tweet { @extend .light; font-family: sans-serif; }" > assets/hugo-tweet/_overrides.scss
# start hugo server
hugo server -D
```

The important files:

`config.toml` adds the tweet component and the anake theme.

```toml
# config.toml
theme = ['hugo-static-tweet', 'ananke']
```


`assets/hugo-tweet/_overrides.scss` explicitly sets a font family and sets the light theme as 
default. 

```scss
// `assets/hugo-tweet/_overrides.scss`
.tweet {@extend .light;font-family: sans-serif;}
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
