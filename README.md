# ResourcePackTools

[![release](https://img.shields.io/github/release/PJZ9n/ResourcePackTools.svg)](https://github.com/PJZ9n/ResourcePackTools/releases)
[![license](https://img.shields.io/badge/License-GPL--v3-green)](https://github.com/PJZ9n/ResourcePackTools/blob/master/LICENSE)

|Virion Library|API Plugin|Example Plugin|
|---|---|---|
|[![](https://poggit.pmmp.io/ci.shield/PJZ9n/ResourcePackTools/ResourcePackTools)](https://poggit.pmmp.io/ci/PJZ9n/ResourcePackTools/ResourcePackTools)|[![](https://poggit.pmmp.io/ci.shield/PJZ9n/ResourcePackTools/ResourcePackToolsPlugin)](https://poggit.pmmp.io/ci/PJZ9n/ResourcePackTools/ResourcePackToolsPlugin)|[![](https://poggit.pmmp.io/ci.shield/PJZ9n/ResourcePackTools/ResourceExample)](https://poggit.pmmp.io/ci/PJZ9n/ResourcePackTools/ResourceExample)

- [日本語](#日本語)
- [English](#English)

## 日本語

## 概要
プラグインから簡単にリソースパックを扱うためのツール(ライブラリ)

## 使用方法
- Virionライブラリとして使用する
- APIプラグインとして使用する

## コード例

### プラグインの製作例
- [ResourceExample](https://github.com/PJZ9n/ResourcePackTools/tree/master/examples/resourceexample)

### ディレクトリ構成
```
plugin.phar(Plugin)/
   ├ resources/
   │   ├ info.png
   │   └ test/
   │       └ server.png
   └ src/
       └ ...
test1.zip(ResourcePack)/
   ├ server.png
   ├ manifest.json
   └ pack_icon.png
```

### リソースパックの生成
```php
$pack = new SimpleResourcePack($this, new Version(1, 0, 0));
$pack->setPackIcon("info.png");
$pack->addFile("test/server.png", "server.png");
$pack->generate($this->getDataFolder() . "test1.zip");
```

### リソースパックの登録
```php
ResourcePack::register($this->getDataFolder() . "test1.zip");
```

### リソースパックのアップデート
リソースパックの中身を変える時は、リソースパックのバージョンを上げてください。

例えば`new Version(1, 1, 0);`

これは、一般的なリソースパック開発と同様です。

一度ダウンロードされたリソースパックはキャッシュされますが、バージョンを上げることによって再ダウンロードされます。

## プラグイン

### コマンド
|コマンド名|説明|パラメータ|権限|エイリアス|プレイヤーのみ|
|---|---|---|---|---|---|
|resourcepack|リソースパックを管理する|---|resourcepacktools.command.resourcepack|rp|いいえ|
|resourcepack register|リソースパックを登録する|\<ファイル名\>|---|r|いいえ|
|resourcepack unregisterbyindex|リソースパックをindexから登録解除する|\<index\>|---|urbi|いいえ|
|resourcepack unregisterbyuuid|リソースパックをuuidから登録解除する|\<uuid\>|---|urbu|いいえ|
|resourcepack list|リソースパックのリストを表示する|pack(p):uuid(u)|---|l|いいえ|

## English

## Overview
Tool (library) for easy use of resource packs from plugins

## How to use
- Use as Virion library
- Use as API Plugin

## Code examples

### Example of plugin
- [ResourceExample](https://github.com/PJZ9n/ResourcePackTools/tree/master/examples/resourceexample)

### Directory structure
```
plugin.phar(Plugin)/
   ├ resources/
   │   ├ info.png
   │   └ test/
   │       └ server.png
   └ src/
       └ ...
test1.zip(ResourcePack)/
   ├ server.png
   ├ manifest.json
   └ pack_icon.png
```

### Generate ResourcePack
```php
$pack = new SimpleResourcePack($this, new Version(1, 0, 0));
$pack->setPackIcon("info.png");
$pack->addFile("test/server.png", "server.png");
$pack->generate($this->getDataFolder() . "test1.zip");
```

### Register ResourcePack
```php
ResourcePack::register($this->getDataFolder() . "test1.zip");
```

### Update ResourcePack
When changing the contents of the ResourcePack, please change the version of the ResourcePack.

e.g.`new Version(1, 1, 0);`

This is similar to general ResourcePack development.

ResourcePack that have been downloaded once will be cached, but will be re-downloaded by increasing the version.

## Plugin

### Command
|command name|description|parameter|permission|alias|only player|
|---|---|---|---|---|---|
|resourcepack|Manage ResourcePack|---|resourcepacktools.command.resourcepack|rp|no|
|resourcepack register|Register the ResourcePack|\<filename\>|---|r|no|
|resourcepack unregisterbyindex|Unregister the ResourcePack by index|\<index\>|---|urbi|no|
|resourcepack unregisterbyuuid|Unregister the ResourcePack by uuid|\<uuid\>|---|urbu|no|
|resourcepack list|Show the ResourcePack list|pack(p):uuid(u)|---|l|no|

