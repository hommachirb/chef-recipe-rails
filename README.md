vagrant-rails-recipe
====================

## Dependency

* VirtualBox: 4.3.20
* Vagrant: 1.7.2
* Cmder: 1.1.4.1
* Ubuntu: 14.04
* Chef: 11.18.0

## Installation

### Git

`Vagrantfile`と`cookbook`をダウンロードします。
OSが`32bit`の場合は`box_url`を`ubuntu-14.04-i386_chef`に変更して下さい。

```
$ git clone https://github.com:hommachirb/chef-recipe-rails.git
$ cd ./chef-recipe-rails
```

`rbenv`の`cookbook`をダウンロードします。
（[berkshelf](http://berkshelf.com/)で収集する方法が便利です。）

```
$ git clone https://github.com/opscode-cookbooks/apt.git ./cookbooks/apt
$ git clone https://github.com/fnichol/chef-ruby_build.git ./cookbooks/ruby_build
$ git clone https://github.com/fnichol/chef-rbenv.git ./cookbooks/rbenv
```

### Vagrant

マシンを構築するとChefのRecipeで`Ruby`の開発環境が構築されます。

```
$ vagrant up
```

ChefのRecipeを再実行するには`provision`コマンドを利用します。

```
$ vagrant provision
```

### Bundler

Railsをインストールして、アプリケーションを作りましょう。

```
$ bundle config --global jobs 4
$ gem install rails --no-rdoc --no-ri
```

`http://192.168.33.30:3000/`にアクセスすると`Welcome`が表示されます。

```
$ rails new rails-example
$ cd rails-example
$ rails server --binding 0.0.0.0
```

## License

* MIT
