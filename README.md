## コンセプト
​
社員旅行などの大勢での旅行のときに
担当者が旅行の情報を管理しやすく、全体に周知しやすいように
WEBで「旅のしおり」を作れるようにしたい。
​
## 技術的な要件・やりたいこと
​
Vue.jsを使い、dataだけを入れ替えればいい感じのデザインになるようにしたい。
pc、スマートフォンからの閲覧を想定し、1カラムのシンプルなデザインに。
デプロイしやすいように1ファイルで構築したい。
のちのちカラーセットを用意して選べる様にしたい。
​
## タスク洗い出し
​
タスクとして起こして、調査内容等はこのmarkdownに残しておく。
(のちのち、readme.mdに使用します。)
​
- [x] タスク洗い出し
- [x] 表示要素の洗い出し
- [x] データ構造作成
- [ ] テーマカラーの選定
- [ ] UIデザイン
- [ ] git branchの作成
- [ ] markup
- [ ] css適応
- [ ] vue.js化
- [ ] sample dataの作成
- [ ] 表示テストとデータ構造の見直し
- [ ] css animation適応
- [ ] deploy先の選定
- [ ] deploy手順作成
- [ ] deploy
- [ ] readme.mdの作成
- [ ] 色を変更できる仕組みを作成
​
## 表示要素の洗い出し
- 表紙
  - タイトル
  - 写真
- 概要
  - キャッチコピー
  - コンセプト
  - 行き先
  - 期間
  - 集合時間場所
  - 持ち物
  - 参加者
    - 写真
    - 名前
    - 連絡先
- スケジュール
  - ○日目
    - タイトル
    - 時間
    - 場所
    - 備考
- 宿泊先
  - 名前
  - 備考
  - 部屋割
- 感想メモ
  - google formのurl
​
## データ構造作成
​
「表示要素の洗い出し」に合わせてvue.jsのdata部分を作成します。
​
```js
data = {
  displayItems: {
    mainVisual: {
      title: "",
      imageSrc: "",
      period: "",
      meetingDateTime: "",
      inventory: [
        { name: "", remarks: "" },
        { name: "", remarks: "" },
      ],
      participants: [
        { name: "", imageSrc: "", contactInfo: "" },
        { name: "", imageSrc: "", contactInfo: "" }
      ]
    },
    summary: {
      catchCopy: "",
      concept: "",
      destination: "",
    },
    // todo data構造再検討
    // 1階層目の配列は日数、2階層目は各スケジュール
    schedule: [
      [ {startTime: "", endTime: "", title: "", place: "", remarks: ""},
        {startTime: "", endTime: "", title: "", place: "", remarks: ""}, ],
      [ {startTime: "", endTime: "", title: "", place: "", remarks: ""},
        {startTime: "", endTime: "", title: "", place: "", remarks: ""}, ],
    ],
    hotel: [
      { name: "", linkUrl: "", remarks: "", },
      { name: "", linkUrl: "", remarks: "", },
      { name: "", linkUrl: "", remarks: "", },
    ],
    // おすすめの場所とか食べ物を表示する奴
    // なんかAPIを作るかも
    recommend: [
      { name: "", imageSrc: "", linkUrl: "", remarks: "" },
      { name: "", imageSrc: "", linkUrl: "", remarks: "" },
    ],
    momory: {
      formUrl: "",
      photos: [
        { imageSrc: "", comment: ""},
        { imageSrc: "", comment: ""},
        { imageSrc: "", comment: ""},
      ]
    },
  },
}
```