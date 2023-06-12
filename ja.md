# @tailwindcss/typography

- [@tailwindcss/typography - Tailwind CSS](https://tailwindcss.com/docs/typography-plugin)

制御できない HTML の美しい文字体裁のデフォルト。

公式の Tailwind CSS Typography プラグインは、Markdown からレンダリングされた HTML や CMS から取得された HTML など、制御していないバニラ HTML に美しいタイポグラフィーのデフォルトを追加するために使用できる散文クラスのセットを提供します。

```html
<article class="prose lg:prose-xl">
  {{ markdown }}
</article>
```

実際の動作を確認するには、Tailwind Play の[ライブ デモ](https://play.tailwindcss.com/uj1vGACRJA?layout=preview)をチェックしてください。

## インストール

npm からプラグインをインストールします。

```sh
npm install -D @tailwindcss/typography
```

次に、プラグインを tailwind.config.js ファイルに追加します。

```js
module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('@tailwindcss/typography'),
    // ...
  ],
}
```

## 基本的な使い方

これで、散文クラスを使用して、標準的な HTML に賢明なタイポグラフィ スタイルを追加できるようになりました。

```html
<article class="prose lg:prose-xl">
  <h1>Garlic bread with cheese: What the science tells us</h1>
  <p>
    For years parents have espoused the health benefits of eating garlic bread with cheese to their
    children, with the food earning such an iconic status in our culture that kids will often dress
    up as warm, cheesy loaf for Halloween.
  </p>
  <p>
    But a recent study shows that the celebrated appetizer may be linked to a series of rabies cases
    springing up around the country.
  </p>
  <!-- ... -->
</article>
```

### グレースケールの選択

このプラグインには、Tailwind にデフォルトで含まれる 5 つのグレー スケールごとにモディファイア クラスが含まれているため、プロジェクトで使用しているグレーに合わせてコンテンツを簡単にスタイル設定できます。

```html
<article class="prose prose-slate">
  {{ markdown }}
</article>
```

完全にデフォルトの Tailwind CSS v2.0 ビルドを使用して生成されたクラスは次のとおりです。

|Class|Gray scale|
| ---- | ---- |
|prose-gray (default)|Gray|
|prose-slate|Slate|
|prose-zinc|Zinc|
|prose-neutral|Neutral|
|prose-stone|Stone|

修飾子クラスは、[マルチクラス修飾子パターン](https://nicolasgallagher.com/about-html-semantics-front-end-architecture/#component-modifiers)とともに使用するように設計されており、基本散文クラスと組み合わせて使用する必要があります。

グレースケール修飾子を追加するときは、必ず散文クラスを含めてください

```html
<article class="prose prose-stone">
  {{ markdown }}
</article>
```

独自のカラー テーマの作成について詳しくは、[カスタム カラー テーマの追加](https://tailwindcss.com/docs/typography-plugin#adding-custom-color-themes)に関するドキュメントを参照してください。

### タイプスケールの適用

サイズ修飾子を使用すると、さまざまなコンテキストに合わせてタイポグラフィの全体的なサイズを調整できます。

```html
<article class="prose prose-xl">
  {{ markdown }}
</article>
```

すぐに使用できる 5 つの異なるタイポグラフィ サイズが含まれています。

|Class|Body font size|
| ---- | ---- |
|prose-sm|0.875rem (14px)|
|prose-base (default)|1rem (16px)|
|prose-lg|1.125rem (18px)|
|prose-xl|1.25rem (20px)|
|prose-2xl|1.5rem (24px)|

これらを Tailwind の[ブレークポイント修飾子](https://tailwindcss.com/docs/responsive-design)と組み合わせて使用すると、さまざまなビューポート サイズでコンテンツの全体のフォント サイズを変更できます。

```html
<article class="prose md:prose-lg lg:prose-xl">
  {{ markdown }}
</article>
```

提供されるサイズ修飾子のすべては、フォント サイズ、見出しの間隔、コード ブロックのパディングなどの関係を含め、可能な限り美しく見えるようにプロのデザイナーによって手作業で調整されています。

サイズ修飾子は、[マルチクラス修飾子パターン](https://nicolasgallagher.com/about-html-semantics-front-end-architecture/#component-modifiers)で使用するように設計されており、基本散文クラスと組み合わせて使用する必要があります。

サイズ修飾子を追加するときは、必ず散文クラスを含めてください

```html
<article class="prose prose-lg">
  {{ markdown }}
</article>
```

含まれているタイプ スケールのカスタマイズについては、[CSS のカスタマイズ](https://tailwindcss.com/docs/typography-plugin#customizing-the-css)に関するドキュメントを参照してください。

## ダークモードへの適応

各デフォルトのカラーテーマには、散文反転クラスを追加することでトリガーできる、手動で設計されたダーク モード バージョンが含まれています。

```html
<article class="prose dark:prose-invert">
  {{ markdown }}
</article>
```

独自のカラー テーマの作成について詳しくは、[カスタム カラー テーマの追加](https://tailwindcss.com/docs/typography-plugin#adding-custom-color-themes)に関するドキュメントを参照してください。

## 要素修飾子

要素修飾子を使用して、コンテンツ内の個々の要素のスタイルを HTML 内で直接カスタマイズします。

```html
<article class="prose prose-img:rounded-xl prose-headings:underline prose-a:text-blue-600">
  {{ markdown }}
</article>
```

これにより、ブランドに合わせてリンクのスタイルを設定したり、画像に境界線の半径を追加したりするなどの作業が簡単になります。

利用可能な要素修飾子の完全なリストは次のとおりです。

|Modifier|Target|
| ---- | ---- |
|prose-headings:{utility}|h1, h2, h3, h4, th|
|prose-lead:{utility}|[class~="lead"]|
|prose-h1:{utility}|h1|
|prose-h2:{utility}|h2|
|prose-h3:{utility}|h3|
|prose-h4:{utility}|h4|
|prose-p:{utility}|p|
|prose-a:{utility}|a|
|prose-blockquote:{utility}|blockquote|
|prose-figure:{utility}|figure|
|prose-figcaption:{utility}|figcaption|
|prose-strong:{utility}|strong|
|prose-em:{utility}|em|
|prose-code:{utility}|code|
|prose-pre:{utility}|pre|
|prose-ol:{utility}|ol|
|prose-ul:{utility}|ul|
|prose-li:{utility}|li|
|prose-table:{utility}|table|
|prose-thead:{utility}|thead|
|prose-tr:{utility}|tr|
|prose-th:{utility}|th|
|prose-td:{utility}|td|
|prose-img:{utility}|img|
|prose-video:{utility}|video|
|prose-hr:{utility}|hr|

これらのモディファイアを hover などの他のモディファイアとスタックする場合、おそらく他のモディファイアを最初に置く必要があります。

```html
<article class="prose prose-a:text-blue-600 hover:prose-a:text-blue-500">
  {{ markdown }}
</article>
```

詳細については、スタックされた[修飾子の順序付け](https://tailwindcss.com/docs/hover-focus-and-other-states#ordering-stacked-modifiers)に関する Tailwind CSS ドキュメントをお読みください。

## 最大幅の上書き

各サイズ修飾子には、コンテンツを可能な限り読みやすく保つように設計された最大幅が組み込まれています。 ただし、これが常に望ましいとは限りません。場合によっては、コンテンツをコンテナーの幅いっぱいに収めたい場合もあります。

このような場合、コンテンツに max-w-none を追加して、埋め込まれた max-width をオーバーライドするだけです。

```html
<div class="grid grid-cols-4">
  <div class="col-span-1">
    <!-- ... -->
  </div>
  <div class="col-span-3">
    <article class="prose max-w-none">
      {{ markdown }}
    </article>
  </div>
</div>
```

## 高度なトピック

## タイポグラフィスタイルを元に戻す

散文スタイルを継承すべきではないコンテンツにマークアップのブロックが埋め込まれている場合は、非散文クラスを使用してサンドボックス化します。

```html
<article class="prose">
  <h1>My Heading</h1>
  <p>...</p>

  <div class="not-prose">
    <!-- Some example or demo that needs to be prose-free -->
  </div>

  <p>...</p>
  <!-- ... -->
</article>
```

現時点では、非散文ブロック内に新しい散文インスタンスをネストすることはできないことに注意してください。

## カスタムカラーテーマの追加

tailwind.config.js ファイルのタイポグラフィ セクションに新しいキーを追加し、css キーの下に色を指定することで、独自のカラー テーマを作成できます。

```js
module.exports = {
  theme: {
    extend: {
      typography: ({ theme }) => ({
        pink: {
          css: {
            '--tw-prose-body': theme('colors.pink[800]'),
            '--tw-prose-headings': theme('colors.pink[900]'),
            '--tw-prose-lead': theme('colors.pink[700]'),
            '--tw-prose-links': theme('colors.pink[900]'),
            '--tw-prose-bold': theme('colors.pink[900]'),
            '--tw-prose-counters': theme('colors.pink[600]'),
            '--tw-prose-bullets': theme('colors.pink[400]'),
            '--tw-prose-hr': theme('colors.pink[300]'),
            '--tw-prose-quotes': theme('colors.pink[900]'),
            '--tw-prose-quote-borders': theme('colors.pink[300]'),
            '--tw-prose-captions': theme('colors.pink[700]'),
            '--tw-prose-code': theme('colors.pink[900]'),
            '--tw-prose-pre-code': theme('colors.pink[100]'),
            '--tw-prose-pre-bg': theme('colors.pink[900]'),
            '--tw-prose-th-borders': theme('colors.pink[300]'),
            '--tw-prose-td-borders': theme('colors.pink[200]'),
            '--tw-prose-invert-body': theme('colors.pink[200]'),
            '--tw-prose-invert-headings': theme('colors.white'),
            '--tw-prose-invert-lead': theme('colors.pink[300]'),
            '--tw-prose-invert-links': theme('colors.white'),
            '--tw-prose-invert-bold': theme('colors.white'),
            '--tw-prose-invert-counters': theme('colors.pink[400]'),
            '--tw-prose-invert-bullets': theme('colors.pink[600]'),
            '--tw-prose-invert-hr': theme('colors.pink[700]'),
            '--tw-prose-invert-quotes': theme('colors.pink[100]'),
            '--tw-prose-invert-quote-borders': theme('colors.pink[700]'),
            '--tw-prose-invert-captions': theme('colors.pink[400]'),
            '--tw-prose-invert-code': theme('colors.white'),
            '--tw-prose-invert-pre-code': theme('colors.pink[300]'),
            '--tw-prose-invert-pre-bg': 'rgb(0 0 0 / 50%)',
            '--tw-prose-invert-th-borders': theme('colors.pink[600]'),
            '--tw-prose-invert-td-borders': theme('colors.pink[700]'),
          },
        },
      }),
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
    // ...
  ],
}
```

その他の例については、内部[スタイル定義](https://github.com/tailwindlabs/tailwindcss-typography/blob/master/src/styles.js)を参照してください。

##デフォルトのクラス名の変更

何らかの理由で散文以外のクラス名を使用する必要がある場合は、プラグインの登録時に className オプションを使用して使用できます。

```js
module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('@tailwindcss/typography')({
      className: 'wysiwyg',
    }),
  ]
  ...
}
```

これで、デフォルトのクラス名内の散文のすべてのインスタンスがカスタム クラス名に置き換えられます。

```html
<article class="wysiwyg wysiwyg-slate lg:wysiwyg-xl">
  <h1>My Heading</h1>
  <p>...</p>

  <div class="not-wysiwyg">
    <!-- Some example or demo that needs to be prose-free -->
  </div>

  <p>...</p>
  <!-- ... -->
</article>
```

## CSSのカスタマイズ

このプラグインによって生成された生の CSS をカスタマイズする場合は、tailwind.config.js ファイルのテーマ セクションのタイポグラフィ キーの下にオーバーライドを追加します。

```js
module.exports = {
  theme: {
    extend: {
      typography: {
        DEFAULT: {
          css: {
            color: '#333',
            a: {
              color: '#3182ce',
              '&:hover': {
                color: '#2c5282',
              },
            },
          },
        },
      },
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
    // ...
  ],
}
```

Tailwind のすべてのテーマのカスタマイズと同様に、テーマ ヘルパーにアクセスする必要がある場合は、タイポグラフィ キーを関数として定義することもできます。

```js
module.exports = {
  theme: {
    extend: {
      typography: (theme) => ({
        DEFAULT: {
          css: {
            color: theme('colors.gray.800'),

            // ...
          },
        },
      }),
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
    // ...
  ],
}
```

カスタマイズは DEFAULT や xl などの特定の修飾子に適用する必要があり、css プロパティの下に追加する必要があります。 カスタマイズは、Tailwind プラグインの作成に使用されるのと同じ [CSS-in-JS 構文](https://tailwindcss.com/docs/plugins#css-in-js-syntax)で作成されます。

各モディファイアの設定の詳細な例については、このプラグインの[デフォルト スタイル](https://github.com/tailwindlabs/tailwindcss-typography/blob/master/src/styles.js)を参照してください。
