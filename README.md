# karaoke-domain-modeling

# これ何
カラオケの料金システムはそれなりに複雑で面白味があるので、ドメインモデリングの練習として結構良いんじゃないか？と思ったので考えてみる。  
ちなみにベースにするのは僕がよく行く某カラオケ店だが、全く同じではないかもしれない。詳しくはないので自信なし。

# 課題
- 時間による料金の決定
  - お客が入室した時間と実際に退出した時間で決定される
    - 最小単位は 30min
      - 15min を区切りとして判定する
      - つまり 15min 未満は計上せず、15min 以上から初めて計上する
    - ただし、延長を除いて最初に予約した時間が最低金額になる
      - 例：延長してから 10min くらい歌って出た場合は延長してない料金になる
  - 日中料金と夜間料金（19時以降）がある
    - 跨いでいる場合も考慮する必要がある
    - 例：18:00 - 20:00 だったら日中料金１時間＋夜間料金１時間の金額
  - 夕方からのフリータイムと一日中のフリータイムがある
- 月日による料金の変動
  - 平日料金と休日料金がある
  - 夏休み / 年末年始は料金が（全ての場合で）上がる
- 人物による料金の変動
  - 通常料金と会員料金がある
  - 学割とシニア割がある
- 飲食物による料金の変動
  - アルコール飲み放題プラン
  - 飲食物を注文することが出来、その料金は最終的に部屋の料金と合算して計算される
- その他
  - 全ての料金は店舗ごとに変わるので後から変更が容易なようにする必要がある
  - 全ての料金変動は割合ではなく、定額の差し引きで考えるとする
