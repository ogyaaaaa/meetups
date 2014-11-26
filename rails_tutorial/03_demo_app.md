# railsチュートリアル
### 3. デモアプリケーション

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

## 2.2 Userリソース
### scaffold
`$ rails generate scaffold User name:string email:string`  
```
      invoke  active_record
      create    db/migrate/20141125144816_create_users.rb
      create    app/models/user.rb
      invoke    test_unit
      create      test/models/user_test.rb
      create      test/fixtures/users.yml
      invoke  resource_route
       route    resources :users
      invoke  scaffold_controller
      create    app/controllers/users_controller.rb
      invoke    erb
      create      app/views/users
      create      app/views/users/index.html.erb
      create      app/views/users/edit.html.erb
      create      app/views/users/show.html.erb
      create      app/views/users/new.html.erb
      create      app/views/users/_form.html.erb
      invoke    test_unit
      create      test/controllers/users_controller_test.rb
      invoke    helper
      create      app/helpers/users_helper.rb
      invoke      test_unit
      create        test/helpers/users_helper_test.rb
      invoke    jbuilder
      create      app/views/users/index.json.jbuilder
      create      app/views/users/show.json.jbuilder
      invoke  assets
      invoke    coffee
      create      app/assets/javascripts/users.js.coffee
      invoke    scss
      create      app/assets/stylesheets/users.css.scss
      invoke  scss
      create    app/assets/stylesheets/scaffolds.css.scss
```

### migrate
`$ bundle exec rake db:migrate`  
```
== 20141125144816 CreateUsers: migrating ======================================
-- create_table(:users)
   -> 0.0015s
== 20141125144816 CreateUsers: migrated (0.0016s) =============================
```

## 2.3 Microposts リソース
### scaffold
`$ rails generate scaffold Micropost content:string user_id:integer`  
```
      invoke  active_record
      create    db/migrate/20141125163003_create_microposts.rb
      create    app/models/micropost.rb
      invoke    test_unit
      create      test/models/micropost_test.rb
      create      test/fixtures/microposts.yml
      invoke  resource_route
       route    resources :microposts
      invoke  scaffold_controller
      create    app/controllers/microposts_controller.rb
      invoke    erb
      create      app/views/microposts
      create      app/views/microposts/index.html.erb
      create      app/views/microposts/edit.html.erb
      create      app/views/microposts/show.html.erb
      create      app/views/microposts/new.html.erb
      create      app/views/microposts/_form.html.erb
      invoke    test_unit
      create      test/controllers/microposts_controller_test.rb
      invoke    helper
      create      app/helpers/microposts_helper.rb
      invoke      test_unit
      create        test/helpers/microposts_helper_test.rb
      invoke    jbuilder
      create      app/views/microposts/index.json.jbuilder
      create      app/views/microposts/show.json.jbuilder
      invoke  assets
      invoke    coffee
      create      app/assets/javascripts/microposts.js.coffee
      invoke    scss
      create      app/assets/stylesheets/microposts.css.scss
      invoke  scss
   identical    app/assets/stylesheets/scaffolds.css.scss
```

### migrate
`$ bundle exec rake db:migrate`  
```
== 20141125163003 CreateMicroposts: migrating =================================
-- create_table(:microposts)
   -> 0.0121s
== 20141125163003 CreateMicroposts: migrated (0.0121s) ========================

```

### validates
app/models/micropost.rb
```
class Micropost < ActiveRecord::Base
  validates :content, length: { maximum: 140 }
end
```
- 文字数制限をかけた(140文字)


### 関連付け
app/models/user.rb
```
class User < ActiveRecord::Base
  has_many :microposts
end
```

app/models/micropost.rb
```
class Micropost < ActiveRecord::Base
  belongs_to :user
  validates :content, length: { maximum: 140 }
end
```
- Userは複数のMicropostsを持つ
- Micropostは1つのUserに紐づく
- UserとMicropostのリレーショナルをはった

### Microposts ViewからUser.nameを参照
app/views/microposts/index.html.erb
```
        <td><%= micropost.content %></td>
        <td><%= micropost.user_id %></td>
        <td><%= micropost.user.name %></td>
        <td><%= link_to 'Show', micropost %></td>
        <td><%= link_to 'Edit', edit_micropost_path(micropost) %></td>
        <td><%= link_to 'Destroy', micropost, method: :delete, data: { confirm: 'Are you sure?' } %></td>
```
- 関連付けしたことにより`micropost.user.name`と書くことによって、micropostからuser.nameを引っ張ってこれるようになったよ





