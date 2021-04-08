# パフォーマンスを意識したWebサービス

## 内容
Webフロントエンド でのパフォーマンスを意識したWebサービス開発を行う。CyberAgentのSpeedHackathonを行いたかったが、APIサーバーが動いていなかった。
Chrome最新版で適切に動けばいいとする。
(SpeedHackathonと同じルール)

## やりたいこと
- APIから取得した画像最適化する。
    - 形式をWebPにする。
    - 画像にサイズを指定する。
- クリックずれ防止（通称:ガタン問題）
    - ex) 遅延して広告が表示されることにより、
    - 本来、ページ遷移のためのボタンを押すはずだったが、広告に飛んでしまう。

## やりたいことを踏まえた実装内容
- ***APIから返ってきた画像にサイズを指定でき、形式がWebPにできる画像変換サービスCloudinaryを利用する。***
- 参考URL: [CyberAgent SpeedHackathon 解説](https://github.com/CyberAgentHack/web-speed-hackathon-online/wiki/Web-Speed-Hackathon-Online-%E5%87%BA%E9%A1%8C%E3%81%AE%E3%81%AD%E3%82%89%E3%81%84%E3%81%A8%E8%A7%A3%E8%AA%AC#%e7%94%bb%e5%83%8f%e3%81%ae%e6%9c%80%e9%81%a9%e5%8c%96)
- デメリット
- Cloudinaryには無料枠がある。
    - 参考URLにも記述されているが、ThumborというOSS の画像 CDN 実装を用いて自前で CDN サーバを構築することができる。
    - しかし、時間がないため、省略。SaaS(CLoudinary)に頼る。
- ***要素の位置を固定することにより、クリックのズレをなくす。***
- 参考URL: https://developers.cyberagent.co.jp/blog/archives/636/



## 実装によるパフォーマンスの変化（LightHouse）