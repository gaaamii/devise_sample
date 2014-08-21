# Deviseのれんしゅう

## Devise
- ユーザー登録・認証のためのgem
- https://github.com/plataformatec/devise

## つかいかた

Gemfileを編集。

```
gem 'devise'
```

インストール。

```
bundle
```

> The generator will install an initializer which describes ALL Devise's configuration options and you MUST take a look at it.

ジェネレータでイニシャライザをインストール。Deviseの設定オプションとかがぜんぶ書かれてる。何がインストールされたか見とくこと。

```
rails generate devise:install
```

> Replace MODEL with the class name used for the application’s users (it’s frequently User but could also be Admin). This will create a model (if one does not exist) and configure it with default Devise modules. The generator also configures your config/routes.rb file to point to the Devise controller.

MODELのとこにモデル名を入れる。UserとかAdminとか。モデルを作ってくれて、Deviseのモジュールにもとづいて設定してくれる。routes.rbの方でDeviseのコントローラとの紐付けもしてくれる。

```
rails generate devise MODEL
```
