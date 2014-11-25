# railsチュートリアル
### 1. プロジェクト作成から起動の確認まで

## 環境
- Mac
- ruby2.0.0  
``$ ruby -v``  
> ``ruby 2.0.0p481 (2014-05-08 revision 45883) [x86_64-darwin13.4.0]``
- rails4.0.5  
``$ rails -v``  
> ``Rails 4.0.5``
- sqlite3.7.13  
``$ sqlite3 --version``  
> ``3.7.13 2012-07-17 17:46:21``

## 1.2.3 最初のアプリケーション
### rails new
1. 作業用ディレクトリ作成  
``$ mkdir rails_tutorial``

2. 作業用ディレクトリに移動  
``$ cd rails_tutorial``

3. rails new  
``$ rails new first_app --skip-bundle``

## 1.2.4 Bundler
### gemのインストール
1. rails newしたディレクトリに移動  
``$ cd first_app``

2. Gemfileの編集  
``$ vi Gemfile``
> [Gemfile]参照


3. Bundleインストール  
``$ bundle install --path vendor/bundle``  
※ Gemfile.lockがあったら削除しておいた方がいい？

-------------------------------------------------------------------------------------------------------------------
> [Gemfile]

```
source 'https://rubygems.org'
ruby '2.0.0'
#ruby-gemset=railstutorial_rails_4_0

# Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
gem 'rails', '4.0.5'

# Use sqlite3 as the database for Active Record
group :development do
  gem 'sqlite3', '1.3.8'
end

# Use SCSS for stylesheets
gem 'sass-rails', '4.0.2'

# Use Uglifier as compressor for JavaScript assets
gem 'uglifier', '2.1.1'

# Use CoffeeScript for .js.coffee assets and views
gem 'coffee-rails', '4.0.1'

# See https://github.com/sstephenson/execjs#readme for more supported runtimes
# gem 'therubyracer', platforms: :ruby

# Use jquery as the JavaScript library
gem 'jquery-rails', '3.0.4'

# Turbolinks makes following links in your web application faster. Read more: https://github.com/rails/turbolinks
gem 'turbolinks', '1.1.1'

# Build JSON APIs with ease. Read more: https://github.com/rails/jbuilder
gem 'jbuilder', '1.0.2'

group :doc do
  # bundle exec rake doc:rails generates the API under doc/api.
  gem 'sdoc', '0.3.20', require: false
end


# Use ActiveModel has_secure_password
# gem 'bcrypt', '~> 3.1.7'

# Use unicorn as the app server
# gem 'unicorn'

# Use Capistrano for deployment
# gem 'capistrano', group: :development

# Use debugger
# gem 'debugger', group: [:development, :test]
```
-------------------------------------------------------------------------------------------------------------------

## 1.2.5 rails server
### rails起動
1. railsの起動  
``$ rails server``  
もしくは  
``$ rails s``  

1. ブラウザで起動の確認  
``http://localhost:3000``  










