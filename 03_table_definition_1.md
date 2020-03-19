# テーブル定義書1

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。

## 全体
- created_at, updated_atの説明が全てユーザ登録日時・更新日時になっている
  > created_at, updated_atの説明が全てユーザ登録日時・更新日時になっています。テーブル名に合わせた表記にしてください。
- created_at, updated_atのデータ型がtimestampでなく、datetimeになっている
  > created_at, updated_atのデータ型をデフォルトのtimestampにしてください。もしdatetimeにする理由があれば教えてください。
- カラム名にテーブル名をつけてる
  > カラム名にテーブル名をつけるのはよくありません。個別に指摘をしているので修正してください。
- PKは全て「id」とすべき
  > PKが「テーブル名_id」ではなく「id」としてください。例えば、呼び出すときにUser.user_idとなり無駄があります。
  (これ人によって指摘ある・ないと別れてるんですがどっちがいいですか)
## Admin
- テーブル名が単数形
  > テーブル名が単数形になっています。テーブル名は全て複数形で記述してください。
- 「admin_id」のPKに○がない。
  > admin_idのPK・AUTO INCREMENTAL・INDEX欄にチェックがありません。これらはデフォルトでつくオプションなので記載お願いします。もし理由があれば教えてください。
- 「admin_email」「admin_password」の「admin_」が不要
  > admin_email・admin_passwordの「admin_」は必要ありません。呼び出すときにAdmin.admin_emailとなり無駄が多いです。
## Users
- 「user_l_name」「user_f_name」「user_l_kana」「user_f_kana」「user_tel」「user_email」「user_password」の「user_」が不要
  > user_l_name・user_f_name・user_l_kana・user_f_kana・user_tel・user_email・user_passwordの「user_」は必要ありません。呼び出すときにUser.user_l_nameとなり無駄が多いです。
- 「user_○_name」「user_○_kana」はそれぞれfirstとlastのことだと思われるが分かりづらい
  > user_l_name・user_l_kana・user_f_name・user_f_kanaの「_l_」「_f_」はそれぞれ「last」「first」の略だと思われるが、分かりづらいため略さず書いてください。
- 「ship_address」とあるが、これだと配送先住所を1つしか持てない
  > ship_addressをカラムとして持つと、一つまでしか持てません。問題ありませんか。
- 「member_status」のデータ型がstringになっている
  > member_statusのデータ型がstringです。どのような値が入るかを想定して、もう一度考えてみてください。
- 「member_status」だと意味が通りづらい。「is_active」などにすべき
  > member_statusというカラムにDEFAULTでfalseを入れています。このとき、退会している・していない、が一目でわかるようなカラム名をもう一度考えてみてください。
- 「user_f_name」「user_f_kana」のNOT NULLに○がない
  > user_f_name・user_f_kanaのNOT NULLに○がありません。これらのカラムにNULLが入っても問題ないか考えてみてください。
- 「zip_code(郵便番号)」「user_tel(電話番号)」のデータ型がintegerになっている(stringにすべき)
  > zip_code・user_telのデータ型がintegerになっています。これらのカラムは整数というよりは文字列(先頭の"0"に意味がある等)なので、stringにしてください。
## Products
- 「products_id」が複数形になっている
  > products_idが複数形になっています。PKは単数形_idとしてください。
- 「disc_id」を持っている
  > disc_idを持っていますが、Diskテーブルとの多重度を考えると必要ありません。
- 「genre_id」「label_id」「artist_id」のFKに○がない
  > genre_id・label_id・artist_idのFK欄にチェックがありません。記述をお願いします。
- 「cd_image」「cd_title」の「cd_」が不要
  > cd_image・cd_titleの「cd_」は必要ありません。Product.image, Product.titleだけで伝わります。
- 「発売日」を格納するカラムがない
  > 発売日はどのように保持しますか。
- 「stock」がある(「在庫数は入荷記録と受注詳細記録から算出する」と異なる)ので削除する
  > stock(在庫数)は他の情報から計算で求めることができます。カラムとして持つ理由があれば教えてください。
- 「stock_status(在庫ステータス)」はあるが「販売ステータス」がない
  > 「stock_status(在庫ステータス)」はありますが「販売ステータス」はありません。要件で記載されているのは前者ではなく後者です。カラム名と説明の変更をお願いします。
## Disks
- 「track_num」がある
  > トラックナンバー(track_num)とは「ディスクの中の曲順」を表すものです。Disksテーブルの中に書くべきか、もう一度考えてみてください。
- 「products_id」が複数形になっている
  > products_idが複数形になっています。単数形_idとしてください。
## Songs, Labels, Artists, Genreまとめて
- PKが存在しない
  > テーブル中に主キー(PK)が存在していません。記述をお願いします。
- 「曲名」や「レーベル名」を格納するカラムの名前が「song」「label」ではわかりづらい。
また、label以外はデータ型がintegerになっている
  > 曲名・レーベル名...を表すカラム名にsong・label...を用いていますが、呼び出すときにSong.songと書かねばならず、非常に分かりづらいです。修正してください。
  > また、song・artist・genreのデータ型がintegerになっています。stringにしてください。
## Labels, Artists, Genresまとめて
- 「products_id」は必要ない
  > products_idが存在していますが、Productsテーブルとの多重度を考えると必要ありません。
## Songs
- 「disc_id」のAUTO INCREMENTALに○がある
  > 外部キー(FK)であるdisc_idのAUTO INCREMENTALにチェックが入っています。本当に必要かもう一度考えてみてください。
- ディスク内の曲順を管理するカラムが必要
  > (Disksの中で指摘しているため省略)
## Genre
- テーブル名が単数形
  > テーブル名は複数形にしてください。
## Cart item, Buy details
- テーブル名の単語の間をスペースで区切っている
  > テーブル名の単語間がスペースで区切られています。単語の先頭を全て大文字にし、スペースを開けないで区切ってください(キャメルケースと言います)。
- 「buy num」がスペース区切りになっている
  > buy numの単語間がスペースで区切られています。アンダーバー("_")で区切ってください(スネークケースと言います)。
## Cart item
- PKが存在しない
  > テーブル中に主キー(PK)が存在していません。記述をお願いします。
- テーブル名が単数形
  > テーブル名は複数形にしてください。
- 「products_id」のデータ型がない
  > products_idのデータ型を記述してください。
- 「products_id」が複数形になっている
  > products_idが複数形になっています。単数形_idとしてください。
- 「subtotal(小計金額)」は不必要
  > subtotal(小計金額)は計算で求めることができます。カラムとして持つ理由があれば教えてください。
## Buy details
- 「buy_details_id」が複数形になっている
  > buy_details_idが複数形になっています。単数形_idとしてください。
- 「buy_id」を持っていない
  > (Buyの中で指摘しているため省略)
- テーブル名を管理者から見た名前にする(受注詳細を意味するOrder_detailsとか)
  > Buy details(購入詳細)はエンドユーザ側に視点をもった命名です。管理者側の視点で命名を考えてください(「受注」詳細を意味するOrder_details等)。
- テーブル名の変更に合わせて「buy_num(購入枚数)」も変更すべき
  > (本当にそうか？怪しくなってきた)
## Buy
- 「buy_details_id」を持っている
  > buy_details_idが存在していますが、Buy detailsテーブルとの多重度を踏まえてこのテーブルに必要か考えてみてください。
- 配送先郵便番号・配送先氏名を持っていない
  > 配送先郵便番号・配送先氏名はどのように管理しますか。
- 「buy_at(購入日)」は不必要
  > buy_at(購入日)は要件にないので不要です。もし、必要であってもcreated_atを用いれば新たにカラムを作る必要はないはずです。
- 「pay」のデータ型がstringだが、enum使うことを考えたらintegerか
  > payのデータ型がstringですが、payには固定された数種類の値しか入らないため"enum"を使うことをおすすめします。
- テーブル名を管理者から見た名前にする(受注を意味するOrdersとか)
  > Buy(購入)はエンドユーザ側に視点をもった命名です。管理者側の視点で命名を考えてください(「受注」を意味するOrders等)。
- 「stock(支払合計)」では意味が一致しない。日本語に合わせたカラム名にする
  > stock(支払合計)はカラム名と説明の意味が一致していません。説明に合わせて、カラム名を考え直してください。
- 「pay(支払い方法)」では意味が一致しない。「方法」を含むカラム名にする
  > pay(支払い方法)はカラム名と説明の意味が一致していません(カラム名が不十分です)。説明に合わせて、カラム名を考え直してください。

**研修担当レビュー**
合格です
一応カラム名にテーブル〜系の指摘は全体でもしておくと良いです。(確認後このメッセージは削除して構いません。)
