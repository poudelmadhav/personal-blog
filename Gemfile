source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
gem 'rake'

gem "rb-fsevent", "~> 0.9.0"

gem "jekyll"

group :jekyll_plugins do
  gem 'jekyll-sitemap'
end
