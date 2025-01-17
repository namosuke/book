# プロトタイプベース\(🚧執筆中\)

ここではJavaScriptのプロトタイプベースを説明します。JavaやPHPなどでクラスを使ってことがある方や、オブジェクト指向プログラミングに触れたことがある方を念頭に書いています。また、ここでは主に次の疑問に答えていきます。

* プロトタイプベースとは何なのか？
* プロトタイプベースのJavaScriptは、PHPやJavaとどう違う？
* なぜJavaScriptはプロトタイプベースを採用したのか？
* プロトタイプベースの利点は何か？

### オブジェクトの生成

オブジェクト指向プログラミング\(OOP\)では、オブジェクトを扱います。オブジェクトを扱う以上は、オブジェクトを生成する必要があります。

しかし、オブジェクトの生成方式は、OOPで統一的な決まりはありません。言語によって異なるのです。言語によりオブジェクト生成の細部は異なりますが、生成方法は大きく分けて「クラスベース」と「プロトタイプベース」があります。

### クラスベース

JavaやPHP、Ruby、Pythonなどはクラスベースに分類されます。クラスベースでのオブジェクト生成は、オブジェクトの設計図である「クラス」を用います。クラスに対して`new`演算子を用いるなどして得られるのがオブジェクトであり、クラスベースの世界では、それを「インスタンス」と呼びます。

たとえば、ボタンのオブジェクトがほしいときは、まずその設計図となるボタンクラスを作ります。

```javascript
class Button {
  constructor(name) {
    this.name = name;
  }
}
```

その上で、ボタンクラスに対して`new`演算子を用いると、ボタンオブジェクトが得られます。

```javascript
dangerousButton = new Button("絶対に押すなよ?");
```

このような言語がクラスベースと言われるのは、オブジェクトの素となるのがクラスだからです。

### プロトタイプベース

一方のJavaScriptのオブジェクト生成はプロトタイプベースです。プロトタイプベースの特徴は、クラスのようなものが無いところです。

クラスベースではオブジェクトの素となるものはクラスでした。プロトタイプベースには、クラスがありません。では、何を素にしてオブジェクトを生成するのでしょうか。答えは、「オブジェクトを素にして新しいオブジェクトを生成する」です。

たとえば、JavaScriptでは既存のオブジェクトに対して、`Object.create()`を実行すると新しいオブジェクトが得られます。

```javascript
const button = {
  name: "ボタン",
};

const dangerousButton = Object.create(button);
dangerousButton.name = "絶対に押すなよ？";
```

上の例の`button`と`dangerousButton`は異なるオブジェクトになります。その証拠に、それぞれの`name`プロパティは値がことなります。

```javascript
console.log(button.name); //=> "ボタン"
console.log(dangerousButton.name); //=> "絶対に押すなよ？"
```

「プロトタイプ」とは日本語では「原型」のことです。プロトタイプベースは単純に言ってしまえば、原型となるオブジェクトを素にオブジェクトを生成するアプローチなのです。

{% hint style="info" %}
#### コラム: プロトタイプベースは直感的でない？

この本を読者の多くは、PHPやJavaなどクラスベースの言語に馴染みが深いかと思います。その立場からすると、プロトタイプベースは直感的でないと感じるかもしれません。ところが、日常生活で私たちはプロトタイプベース的な活動をしていることがあります。ここでは、プロトタイプベースが少しでも身近に感じれるよう、ちょっとした例え話をしたいと思います。

仕事などで書類を作成することは無いでしょうか。会議の議事録、テスト仕様書、報告書、経費精算書…。いろいろあると思います。中には定期的、または不定期に同じような書類を何度か作ることもあるでしょう。みなさんは繰り返しのペーパーワークをどうこなしていますか。

準備のいい人は、雛形を作っておくことでしょう。雛形とは、いつも変わらない部分は埋めておき、毎度内容が変わる部分は空欄にした文書のことです。いざ書類が必要になったときは、雛形をベースに穴埋めすれば書類ができます。このやり方はクラスベースに似ています。クラスはそのままでは使えませんが、インスタンス化すると使えます。書類の雛形もそのままでは提出できませんが、穴埋めすれば役立ちます。

一方で、書類の準備の時間がないときや、準備のモチベーションが上がらないときは、雛形までは作らないかもしれません。それでも、前回使った書類があれば、それを複製して今回必要になることに合わせて内容を加筆したり、置き換えたりしてしあげてしまうことはありませんでしょうか。このアプローチはプロトタイプベースに似ています。プロトタイプとなるオブジェクトはそれ自身も使えますし、それを素にした新しいオブジェクトももちろん使えます。前回使った書類はそれ自身で役に立っていますが、それを複製して作った新しい書類も役に立ちます。
{% endhint %}

{% hint style="warning" %}
TODO: 続きを書く
{% endhint %}

