# パフォーマンスを意識したWebサービス

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

## 