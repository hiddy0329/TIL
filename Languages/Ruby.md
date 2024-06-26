# Rubyとは

- 全てがオブジェクト
- シンプルな文法
- 豊富な日本語ドキュメント
- 強力な標準ライブラリ
- 美しい記法

# Rubyの作法

## 変数と定数

- 変数と定数については公式マニュアルを参考にすると以下のような記法が推奨される。[Rubyリファレンスマニュアル](https://docs.ruby-lang.org/ja/latest/doc/spec=2fvariables.html)

  - ローカル変数
    - ローカル変数は基本的に「ローワースネークケース」で記述する。
    ```
    name = 'Jhon'
    basic_income = 1000
    ```
  - インスタンス変数
    - インスタンス変数は先頭に「@」をつけて記述する。
    ```
    @name = 'Jhon'
    @basic_income = 1000
    ```
  - グローバル変数
    - グローバル変数は先頭に「$」をつけて記述する。
    ```
    $name = 'Jhon'
    ``` 
  - クラス定数
    - クラス定数は先頭に「@@」をつけて記述する。
    ```
    class Hoge
      @@hoge = 1
      def bar
        puts @@hoge
      end
    end
    ```
  - 定数
    - 定数は全て大文字で記述する。
    ```
    TAX = 1.8
    ```


# Rubyと多言語との違い

- [多言語からのRuby入門](https://www.ruby-lang.org/ja/documentation/ruby-from-other-languages/)
