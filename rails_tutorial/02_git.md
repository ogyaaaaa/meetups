# railsチュートリアル
### 2. Githubでバージョン管理をスタートさせる

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

# 1.3 Gitによるバージョン管理
## 1.3.1 インストールとセットアップ
### Gitの設定
'1. 現在の設定確認  
``$ git config --global --list``  
> ``user.name=tarou yamada``  
> ``user.email=t-yamada@nexceed.co.jp`` 

'2. 設定されていなければ  
``$ git config --global user.name "あなたの名前"``  
``$ git config --global user.email your.email@example.com``

'3. エイリアス設定
`checkout` という長ったらしいコマンドの代わりにcoという短いコマンド (エイリアス) も使えるようにしています。  
これを行うには以下を実行します。  
``$ git config --global alias.co checkout``

'4. 最初のリポジトリセットアップ  
``$ git init``

'5. git管理対象ファイルの設定  
``$ vi gitignore``
```
# Ignore bundler config.
/.bundle

# Ignore the default SQLite database.
/db/*.sqlite3
/db/*.sqlite3-journal

# Ignore all logfiles and tempfiles.
/log/*.log
/tmp

# Ignore other unneeded files.
/vendor
doc/
*.swp
*~
.project
.DS_Store
.idea
.secret
```

'6. バージョン管理対象の確認  
``$ git status``  
```
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	Gemfile
	Gemfile.lock
	README.rdoc
	Rakefile
	app/
	bin/
	config.ru
	config/
	db/
	lib/
	log/
	public/
	test/

nothing added to commit but untracked files present (use "git add" to track)
```

## 1.3.2 追加とコミット
'7. Gitに追加  
``$ git add .``  

'8. 確認  
``$ git status``  
```
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   .gitignore
	new file:   Gemfile
	new file:   Gemfile.lock
	new file:   README.rdoc
	new file:   Rakefile
	new file:   app/assets/images/.keep
	new file:   app/assets/javascripts/application.js
	new file:   app/assets/stylesheets/application.css
	new file:   app/controllers/application_controller.rb
	new file:   app/controllers/concerns/.keep
	new file:   app/helpers/application_helper.rb
	new file:   app/mailers/.keep
	new file:   app/models/.keep
	new file:   app/models/concerns/.keep
	new file:   app/views/layouts/application.html.erb
	new file:   bin/bundle
	new file:   bin/rails
	new file:   bin/rake
	new file:   config.ru
	new file:   config/application.rb
	new file:   config/boot.rb
	new file:   config/database.yml
	new file:   config/environment.rb
	new file:   config/environments/development.rb
	new file:   config/environments/production.rb
	new file:   config/environments/test.rb
	new file:   config/initializers/backtrace_silencers.rb
	new file:   config/initializers/filter_parameter_logging.rb
	new file:   config/initializers/inflections.rb
	new file:   config/initializers/mime_types.rb
	new file:   config/initializers/secret_token.rb
	new file:   config/initializers/session_store.rb
	new file:   config/initializers/wrap_parameters.rb
	new file:   config/locales/en.yml
	new file:   config/routes.rb
	new file:   db/seeds.rb
	new file:   lib/assets/.keep
	new file:   lib/tasks/.keep
	new file:   log/.keep
	new file:   public/404.html
	new file:   public/422.html
	new file:   public/500.html
	new file:   public/favicon.ico
	new file:   public/robots.txt
	new file:   test/controllers/.keep
	new file:   test/fixtures/.keep
	new file:   test/helpers/.keep
	new file:   test/integration/.keep
	new file:   test/mailers/.keep
	new file:   test/models/.keep
	new file:   test/test_helper.rb
```

'9. `git add .` を全て取り消したい場合は？  
``$ git reset``  
※ `$ git remote -v` || `$ git branch -a` とかで確認してからの方がいいかも？

'10. コミット  
``$ git commit -m "Initialize repository"``  
```
[master (root-commit) affd0c4] Initialize repository
 51 files changed, 834 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock
 create mode 100644 README.rdoc
 create mode 100644 Rakefile
 create mode 100644 app/assets/images/.keep
 create mode 100644 app/assets/javascripts/application.js
 create mode 100644 app/assets/stylesheets/application.css
 create mode 100644 app/controllers/application_controller.rb
 create mode 100644 app/controllers/concerns/.keep
 create mode 100644 app/helpers/application_helper.rb
 create mode 100644 app/mailers/.keep
 create mode 100644 app/models/.keep
 create mode 100644 app/models/concerns/.keep
 create mode 100644 app/views/layouts/application.html.erb
 create mode 100755 bin/bundle
 create mode 100755 bin/rails
 create mode 100755 bin/rake
 create mode 100644 config.ru
 create mode 100644 config/application.rb
 create mode 100644 config/boot.rb
 create mode 100644 config/database.yml
 create mode 100644 config/environment.rb
 create mode 100644 config/environments/development.rb
 create mode 100644 config/environments/production.rb
 create mode 100644 config/environments/test.rb
 create mode 100644 config/initializers/backtrace_silencers.rb
 create mode 100644 config/initializers/filter_parameter_logging.rb
 create mode 100644 config/initializers/inflections.rb
 create mode 100644 config/initializers/mime_types.rb
 create mode 100644 config/initializers/secret_token.rb
 create mode 100644 config/initializers/session_store.rb
 create mode 100644 config/initializers/wrap_parameters.rb
 create mode 100644 config/locales/en.yml
 create mode 100644 config/routes.rb
 create mode 100644 db/seeds.rb
 create mode 100644 lib/assets/.keep
 create mode 100644 lib/tasks/.keep
 create mode 100644 log/.keep
 create mode 100644 public/404.html
 create mode 100644 public/422.html
 create mode 100644 public/500.html
 create mode 100644 public/favicon.ico
 create mode 100644 public/robots.txt
 create mode 100644 test/controllers/.keep
 create mode 100644 test/fixtures/.keep
 create mode 100644 test/helpers/.keep
 create mode 100644 test/integration/.keep
 create mode 100644 test/mailers/.keep
 create mode 100644 test/models/.keep
 create mode 100644 test/test_helper.rb
```

'11. コミットメッセージの履歴を参照  
``$ git log``  
```
commit affd0c49dfea5c8d7c7ff2e5658e4163d2d4a84c
Author: torou yamada <t-yamada@nexceed.co.jp>
Date:   Mon Nov 24 06:09:53 2014 +0900

    Initialize repository
```

## 1.3.4 GitHub
'12. リポジトリの作成  
`Create repository` して、リポジトリを作成する

'13. GitHubに `first_app` を `push` する  
`$ git remote add origin https://github.com/username/first_app.git`  
確認  
`$ git remote -v`  
> `origin	https://github.com/username/first_app.git (fetch)`  
> `origin	https://github.com/username/first_app.git (push)`  

`push` する  
`$ git push -u origin master`  
```
Counting objects: 58, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (48/48), done.
Writing objects: 100% (58/58), 14.28 KiB | 0 bytes/s, done.
Total 58 (delta 2), reused 0 (delta 0)
To https://github.com/username/first_app.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
```

'14. GitHubで確認




