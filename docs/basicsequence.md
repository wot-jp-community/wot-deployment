# 基本シーケンス

Web of Thingsでは、IoTデバイスとの相互作用をProperty、Action、
Eventの3つに抽象化しています。理論的には、これらの相互作用に
対して記述可能な任意のプロトコルを利用することができますが、
ここではHTTPを使った場合の典型的なシーケンスとThing Descriptionの記述を示します。

## Property

Propertyでは、Thingがもつ属性値を読み書きする操作を記述します。
温度センサが保持している現在温度の値を読んだり、LEDの点灯状態を書き換えることで
LEDを点灯させたりする操作がこれにあたります。

Propertyのシーケンス例を下記に示します。

![Propertyのシーケンス例](images/seq-property.svg)

Consumerは、GETリクエストで属性値を読み、PUTリクエストで書き込みます。
データ形式はJSONを用いるのが一般的です。上記の相互作用の仕方を
Thing Descriptionで記載すると下記のようになります(properties部分のみ抜粋)。

```JSON
{
    //...
    "properties": {
        "ledstatus": {
            "type": "object",
            "properties": {
                "state": {
                    "type": "boolean"
                }
            },
            "forms": [{
                "href": "https://mylamp.example.com/led"
            }]
        }
    }
    //...
}

```
この記述は:
- このThingは"ledstatus"という属性をもつ
- その属性値は`{"status": trueまたはfalse}`という値をもつ
- その属性値は読み書き可能である(デフォルト値より)
- アクセスするには`https://mylamp.example.com/led`を使う
- 属性値を読む際のHTTPメソッドは`GET`(デフォルト値より)
- 属性値を書く際のHTTPメソッドは`PUT`(デフォルト値より)
- ペイロードのタイプは`application/json`形式(デフォルト値より)

ということを意味しています。


## Action

Actionでは、Thingに対してなんらかの動作を指示したり、Thingが持つ機能を実行させる操作を記述します。
例えば、LEDランプのスイッチをトグルする、スピーカから合成音声を音声を鳴らす、といった操作がこれにあたります。

Actionのシーケンス例を下記に示します。

![Actionのシーケンス例](images/seq-action.svg)

ここでは、ConsumerがPOSTリクエストでLEDのランプのスイッチをトグルしています。
POSTリクエストと返答に含まれるボディ部は使っていません。
この相互作用の仕方をThing Descriptionで記述すると下記のようになります。

```JSON
{
    //
    "actions": {
        "toggle": {
            "forms": [{
                "href": "https://mylamp.example.com/toggle"
            }]
        }
    }
}

```
この記述は:
- このThingは"toggle"というアクションを受け付ける
- このアクションの起動によってThingの属性値が変わる可能性がある(デフォルト値より)
- このアクションの起動は冪等(idempotent)な操作ではない(デフォルト値よる)
- アクションを起動する際のHTTPメソッドは`POST`(デフォルト値より)

ということを意味しています。

なお、ここではPOSTメソッドでアクションを実行していますが、Thingの実装によっては属性値の取得(GET)を契機にアクションを起動したり、属性値を書き換える(PUT)ことによってアクションを起動することがあるかもしれません。
この場合、前節で述べたpropertyの読み書きとしてアクションを記述することもできますが、
Thingの利用者にとってそれがなんらかの動作として抽象化した方がいい場合はアクションとして記述することをお勧めします。
たとえば、`https://mylamp.example.com/invokeaction`というURLにPUTリクエストで`{"action": "toggle"}`を書き込むと
動作が起動する場合、書き込み可能な属性値として抽象化するより、アクションの起動として抽象化したほうが
Thingの利用者にわかりやすくなります。
このような場合のThing Descriptionの記述は下記のようになります。
```JSON
{
    // ...
    "actions": {
        "toggle": {
            "input": {
                "type": "object",
                "properties": {
                    "action": {
                        "const": "toggle"
                    }
                }
            },
            "forms": [{
                "href": "https://mylamp.example.com/invokeaction",
                "htv:methodName": "PUT"
            }]
        }
    }
}
```

## Event

TBD

