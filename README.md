# [picnic](http://timmliu.github.io/picnic/)
A simple picnic planner.

## Jekyll initial custom setup instructions:
Install Jekyll according to [http://jekyllrb.com/](http://jekyllrb.com/):

```
$ gem install jekyll
$ jekyll new picnic
$ cd picnic
```

### Gem setup:
- Create a Gemfile in the project folder with the following:

```
source 'https://rubygems.org'

gem 'bourbon'
gem 'coffee-script'
gem 'jekyll'
gem 'jekyll-assets'
gem 'jekyll-haml'
gem 'neat'
gem 'sass'
gem 'uglifier'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
```

- Then run `bundle install`

### Set/add the following to `_config.yml`:

```
baseurl: /picnic
exclude: [Gemfile, Gemfile.lock, README.md]
```

### To build and deploy to Github pages:
* Remove `_site` from .gitignore

`$ jekyll build`
`$ git add _site && git commit -m "Initial _site subtree commit"`
`$ git subtree push --prefix _site origin gh-pages && git push origin master`

**To delete gh-pages and re-push:**
`$ git push origin git subtree split --prefix _site gh-pages:gh-pages --force`
`$ jekyll build`
`$ git subtree push --prefix _site origin gh-pages && git push origin master`

* If needed, replace `_site` in above commands with the name of your build folder.
