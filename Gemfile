source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(::URI.open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
gem 'rake'

gem "rb-fsevent"

gem "jekyll"

group :jekyll_plugins do
  gem 'jekyll-sitemap'
  gem 'jekyll-seo-tag'
  gem 'jekyll-admin'
end
