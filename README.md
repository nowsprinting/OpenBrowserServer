# VRChatからURLを開くシステム
## これは何？
VRChat内でのトリガーで、既定のブラウザからWEBページを開くことを想定したソフトウェアです。

## 使い方
開きたいURLを引数にした起動用URLをVRChat内からHTTP GETします。

```
http://localhost:50505/openURL/
```

上記を起動用URLと呼びます。

起動用URLの後ろに開きたいURLを指定します。引数と呼びます。  
例:

```
http://localhost:50505/openURL/https://www.yukiyukivirtual.net/  
```

- 引数のURLのドメイン部分は必ず/で終わる必要があります。
- 引数の#以降は無視されます。#を使いたい場合は、#を%23に置き換えてください。

## 起動
exeを実行します。

## 終了
起動時に表示されるウィンドウ上で *Ctrl+C* を入力します。

## 設定
*setting.yaml* を編集します。テキストエディタで編集できます。

### 構文
```yaml
Port: 50505
IdlePeriod: 1000
Protocol:
  - https
Domain:
  - yukiyukivirtual.net
  - booth.pm
```

### ポート番号
VRChat内から呼び出す際のポート番号を設定します。通常は互換性のために *50505* を使用してください。
この設定は起動時に有効になります。

```yaml
Port: 50505
```

### 休止期間
先のリクエストから次回のリクエストまでの時間を設定します。短い間隔で大量のリクエストが来た時に、この間隔以内のリクエストは無視されます。
正のミリ秒単位で設定してください。不正な値を設定するとリクエストを常に無視します。
この設定は保存することで即座に有効になります。

```yaml
IdlePeriod: 1000
```

### プロトコル
許可するプロトコルを指定します。デフォルトではhttpsのみ許可されています。
httpや、その他のプロトコルを許可する場合は下記のような構文で追記してください。
この設定は保存することで即座に有効になります。

```yaml
Protocol:
  - https
  - http
```

### ドメイン名
開くことが出来るドメイン名を指定します。
サブドメインはこの設定に含まれます。（例：yukiyukivirtual.booth.pmはbooth.pmに含まれます）

ユーザー側で追加したい場合は下記のような構文で追記してください。
この設定は保存することで即座に有効になります。

```yaml
Domain:
  - yukiyukivirtual.net
  - booth.pm
```

※このシステムは、Boothなどのページを表示するために使用されることを想定しているため、この仕様が不都合になることはないと信じています。

## 免責
このアプリを使用して発生したいかなる障害について、製作者は責任を負いません。

## 問い合わせ
https://github.com/YukiYukiVirtual/OpenBrowserServer/issues

不具合報告、デフォルトで許可してほしいドメイン名はここに報告お願いします。ツールが動作を停止した場合は、ツールに表示されているログもください。ツイッターでも一応受け付けます。
