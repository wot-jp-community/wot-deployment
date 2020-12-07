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

TBD

## Event

TBD

