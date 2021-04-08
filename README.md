# パフォーマンスを意識したWebサービス
参考URL: https://dog-matome-web.netlify.app/

## 作るサービス
犬の画像をたくさん確認できるサービス、ワンチャンまとめ。
Dog APIを使って、大量(50枚以上)に画像を取得するため、パフォーマンスの最適化が必要。

## 内容
Webフロントエンド でのパフォーマンスを意識したWebサービス開発を行う。CyberAgentのSpeedHackathonを行いたかったが、APIサーバーが動いていなかった。
Chrome最新版で適切に動けばいいとする。
(SpeedHackathonと同じルール)

## やりたいこと
- **APIから取得した画像最適化する。**
    - 形式をWebPにする。
    - 画像にサイズを指定する。
- **クリックずれ防止（通称:ガタン問題）**
    - ex) 遅延して広告が表示されることにより、
    - 本来、ページ遷移のためのボタンを押すはずだったが、広告に飛んでしまう。
- **クリックズレが起きている動画**
![demo](https://gyazo.com/15d504a1ab536b1f7a1b2fcc2ca85bab/raw)

## やりたいことを踏まえた実装内容
- **APIから返ってきた画像にサイズを指定でき、形式がWebPにできる画像変換サービスCloudinaryを利用する。**
    - 参考URL: [CyberAgent SpeedHackathon 解説](https://github.com/CyberAgentHack/web-speed-hackathon-online/wiki/Web-Speed-Hackathon-Online-%E5%87%BA%E9%A1%8C%E3%81%AE%E3%81%AD%E3%82%89%E3%81%84%E3%81%A8%E8%A7%A3%E8%AA%AC#%e7%94%bb%e5%83%8f%e3%81%ae%e6%9c%80%e9%81%a9%e5%8c%96)
    - デメリット
    - Cloudinaryには無料枠がある。
        - 参考URLにも記述されているが、ThumborというOSS の画像 CDN 実装を用いて自前で CDN サーバを構築することができる。
        - しかし、時間がないため、省略。SaaS(CLoudinary)に頼る。
- **要素の位置を固定することにより、クリックのズレをなくす。**
    - 参考URL: https://developers.cyberagent.co.jp/blog/archives/636/



## 実装によるパフォーマンスの変化（LightHouse）
### 画像最適化改善前のパフォーマンス
![](https://res.cloudinary.com/kasiwa/image/upload/v1617897295/github/performance.png) 
- やはり、画像形式をWebPに指定し、画像サイズを指定していなければ、少し重そう。

### LazyLoad + 画像形式変更後のパフォーマンス
![](https://res.cloudinary.com/kasiwa/image/upload/v1617898329/github/performance_Fixed.png)
- 大量の画像を読み込むによるパフォーマンスの低下は画像形式をWebPに変更し、LazyLoadを実装したことにより、かなりマシになったっぽい。

## ガタン問題への対処
### 改善前
![](https://gyazo.com/76b1ab668025b237ba3c00180f2812b0/raw)
- どうしても、画像が読み込まれることで、ボタンのクリックがずれる可能性がある。
### 改善後
![](https://gyazo.com/17343c25bf7a71cf68da2994e08ff567/raw)
- 単純に、画像を覆っているdiv要素に高さを指定することでズレを防ぐことができた。
- どうやら、WEBページが画像などの読み込みにより、初回読み込み時とコンテンツの位置がズレる現象をCLSというらしい。

参考URL: [CLSとは](https://www.start-point.net/blog/web/html/cls/)
[Google社員のTwitter:CLSの解説動画](https://twitter.com/addyosmani/status/1276779799198007301?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1276779799198007301%7Ctwgr%5E%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fwww.start-point.net%2Fblog%2Fweb%2Fhtml%2Fcls%2F)

## 今後行いたいこと
- **ThumborというOSSの画像CDN実装を用いて自前でCDNサーバを構築する**
- **ライブラリの削減**
    - ReactではPreactという軽量パッケージがあるが、Vue(Nuxt.js)にもあるかもしれない。
    - パフォーマンスを考える上でライブラリの削減からは逃げられないので、補っておきたい。

## 総評
今回、CyberAgentのSpeedHackathonを行う代わりに、自分で外部APIから取得した大量の画像を読み込むパフォーマンス改善を行った。

画像最適化、ガタン問題対処といった行いたいパフォーマンス改善はできた。しかし、SpeedHackathonで行うWebpack周りの調整、ライブラリの削減等を行えなかった。今後はパフォーマンス周りのイベントに積極的に参加していこう思う。