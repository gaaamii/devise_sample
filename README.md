# Deviseのれんしゅう

## Devise
- ユーザー登録・認証のためのgem
- https://github.com/plataformatec/devise

## つかいかた

### Gemfileを編集

```
gem 'devise'
```

### インストール

```
bundle
```

> The generator will install an initializer which describes ALL Devise's configuration options and you MUST take a look at it.

ジェネレータでイニシャライザをインストール。Deviseの設定オプションとかがぜんぶ書かれてる。何がインストールされたか見とくこと。

```
rails generate devise:install
```

`config/initializers/devise.rb`でDeviseの設定ができて、`config/locales/devise.en.yml`を見てみると、サインイン時の文言とかそういうのが書かれている。

### モデル生成

> Replace MODEL with the class name used for the application’s users (it’s frequently User but could also be Admin). This will create a model (if one does not exist) and configure it with default Devise modules. The generator also configures your config/routes.rb file to point to the Devise controller.

MODELのとこにモデル名を入れる。UserとかAdminとか。モデルを作ってくれて、Deviseのモジュールにもとづいて設定してくれる。routes.rbの方でDeviseのコントローラとの紐付けもしてくれる。

```
rails generate devise MODEL
```

```
rake db:migrate
```

`rake routes`で確認すると、こんなルーティングをしてくれているのがわかる。

```
                  Prefix Verb   URI Pattern                    Controller#Action
        new_user_session GET    /users/sign_in(.:format)       devise/sessions#new
            user_session POST   /users/sign_in(.:format)       devise/sessions#create
    destroy_user_session DELETE /users/sign_out(.:format)      devise/sessions#destroy
           user_password POST   /users/password(.:format)      devise/passwords#create
       new_user_password GET    /users/password/new(.:format)  devise/passwords#new
      edit_user_password GET    /users/password/edit(.:format) devise/passwords#edit
                         PATCH  /users/password(.:format)      devise/passwords#update
                         PUT    /users/password(.:format)      devise/passwords#update
cancel_user_registration GET    /users/cancel(.:format)        devise/registrations#cancel
       user_registration POST   /users(.:format)               devise/registrations#create
   new_user_registration GET    /users/sign_up(.:format)       devise/registrations#new
  edit_user_registration GET    /users/edit(.:format)          devise/registrations#edit
                         PATCH  /users(.:format)               devise/registrations#update
                         PUT    /users(.:format)               devise/registrations#update
                         DELETE /users(.:format)               devise/registrations#destroy
```

### ビューをいじる
Deviseはビューまで生成してくれるけれど、これをそのまま使うことはほぼ無いと思う。これを修正する。

```
rails generate devise:views
```

このコマンドを打つとビューのファイルが`app/views/`以下に生成される。

```
      invoke  Devise::Generators::SharedViewsGenerator
      create    app/views/devise/shared
      create    app/views/devise/shared/_links.erb
      invoke  form_for
      create    app/views/devise/confirmations
      create    app/views/devise/confirmations/new.html.erb
      create    app/views/devise/passwords
      create    app/views/devise/passwords/edit.html.erb
      create    app/views/devise/passwords/new.html.erb
      create    app/views/devise/registrations
      create    app/views/devise/registrations/edit.html.erb
      create    app/views/devise/registrations/new.html.erb
      create    app/views/devise/sessions
      create    app/views/devise/sessions/new.html.erb
      create    app/views/devise/unlocks
      create    app/views/devise/unlocks/new.html.erb
      invoke  erb
      create    app/views/devise/mailer
      create    app/views/devise/mailer/confirmation_instructions.html.erb
      create    app/views/devise/mailer/reset_password_instructions.html.erb
      create    app/views/devise/mailer/unlock_instructions.html.erb
```

上のようにerbファイルが作られるけど、hamlとかslimにしたい場合の対処もある。

#### erbをhamlに変換
- http://docs.komagata.org/4795

#### erbをslimに変換
- http://www.mocchiblog.com/?p=14680


