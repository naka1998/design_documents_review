# テーブル定義書2

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を全体, 共通, などとしてください。

## 全体
- テーブル名は先頭大文字にする
  > テーブル名は先頭大文字かつ複数形で書いてください。
- created_at, updated_atのデータ型がtimestampでなくdatetimeになっている
  > created_at, updated_atのデータ型はデフォルトのtimestampにしてください。意図的であれば理由を教えてください。
- 入荷を表すテーブルが存在しない
  > 入荷を表すテーブルが存在していません。どのように入荷を管理しますか。
- PKは全て「id」とすべき
  > PKが「テーブル名_id」ではなく「id」としてください。例えば、呼び出すときにUser.user_idとなり無駄があります。
## admins
- admin_email, admin_passwordのadmin_は不要
  > admin_email, admin_passwordの「admin_」は不要です。呼び出すときにAdmin.admin_emailとなり無駄があります。
- admin_idのINDEXに○がない
  > 主キー(PK)であるadmin_idはデフォルトでINDEXがつくため、○をつけてください。もしつけない理由があれば教えてください。
## users
- member_statusのデータ型がinteger/enumとあるのに、DEFAULTはfalse
 - 退会している OR していない、のはずなのでデータ型をbooleanにすべき
 - booleanにする場合、カラム名はis_hogehogeにするのがよい
  > member_statusのデータ型がinteger/enumです。退会している OR していないなのでbooleanにしてください。
  > また、booleanにした場合、カラム名は「is_〇〇」(今であればis_deleted等)とするのが良いです。
- user_l_name, user_f_name, user_l_kana, user_f_kana, user_tel, user_email, user_passwordのuser_は不要
  > user_l_name, user_f_name, user_l_kana, user_f_kana, user_tel, user_email, user_passwordの「user_」は不要です。
- user_l_name, user_f_name, user_l_kana, user_f_kanaの「l_」「f_」は、それぞれ「last_」「first_」にすべき(省略すべきでない)
  > user_l_name, user_f_name, user_l_kana, user_f_kanaの「l_」「f_」は、それぞれ「last_」「first_」と省略せずに書いてください、
## ships
- ship_name, ship_address, ship_tel, ship_codeのship_は不要
  > ship_name, ship_address, ship_tel, ship_codeの「ship_」は不要です。
- ship_idのINDEXに○がない
  > 主キーであるship_idはデフォルトでINDEXがつくため、INDEX欄に○をつけてください。
## products
- products_idが複数形になっている
  > (問題指摘時は言われなかったが、『PKは全て「id」とすべき』という上述の指摘とかぶる)
- disc_idは不要
  > disc_idを持っていますが、Diskテーブルとの多重度を考えると必要ありません。
- 「商品名」を表すカラム名をcd_titleとするのは不適
  > cd_titleの「cd_」は必要ありません。Product.titleだけで意味が伝わることを確認してください。
- 要件「在庫数は入荷記録と受注詳細記録から算出する」より、stockは不要
  > stock(在庫数)は他の情報から計算で求めることができます。カラムとして持つ理由があれば教えてください。
- 「stock_status(在庫ステータス)」を表すカラムは不要
 - 「販売ステータス」を表すカラムは必要
  > 「stock_status(在庫ステータス)」はありますが「販売ステータス」がありません。要件で記載されているのは前者ではなく後者です。カラム名と説明の変更をお願いします。
## discs
- products_idが複数形
  > products_idが複数形になっています。単数形_idとしてください。
- disc_numのdisc_は不要
  > disc_numの「disc_」は不要です。
- disc_idのINDEXに○がない
  > 主キーであるdisc_idはデフォルトでINDEXがつくため、INDEX欄に○を記載してください。
## songs
- 曲名を格納するカラム名としてsongは不適(nameにすべき)
## labels
- レーベル名を格納するカラム名としてlabelは不適(nameにすべき)
## aritists
- アーティスト名を格納するカラム名としてartistは不適(nameにすべき)
## genres
- ジャンル名を格納するカラム名としてgenreは不適(nameにすべき)
 > (上4つの指摘まとめて) レコードの名前を保存するカラムとして、テーブル名をそのまま使うのは適切ではありません(呼び出すときにSong.songのようになり意味不明です)。nameのようなカラム名を用いてください。
## cart items
- テーブル名の単語区切りがスペースになっている
  > テーブル名の単語間がスペースで区切られています。CartItemsのようにキャメルケースで書いてください。
- Cart item_idはカラム名として不適(先頭大文字・単語区切りがスペース)。cart_item_idとすべき
  > Cart item_idは先頭大文字・単語間がスペースのためカラム名としてよくありません。cart_item_idとしてください。
- Cart item_idのINDEXに○がない
  > 主キーであるCart item_idはデフォルトでINDEXがつくため、INDEX欄に○を記載してください。 
- products_idが複数形になっている
  > products_idが複数形になっています。単数形_idとしてください。
- buy numの「buy 」は不要
  > buy numの「buy 」は必要ありません。
## sell_details
- sell_details_Idが複数形になっている、「I」が大文字になっている
  > (PKはidとするため省略)
- products_idが複数形になっている
  > products_idが複数形になっています。単数形_idとしてください。
- products_idのFKに○がない
  > products_idのFKの欄に○をつけてください。
- sell_numのsell_は不要
  > sell_numの「sell_」は必要ありません。
- FKとしてsell_idがない
  > (sellsで指摘しているため省略)
- 「購入価格」を表すカラムがない
  > 購入価格はどのように保持しますか。
## sells
- sell_details_Idは不要
  > sell_details_Idを持っていますが、多重度を考えると必要ありません。
- 「支払い方法」を表すカラム名として、payでは「方法」を表せていない
  > pay(支払い方法)はカラム名が説明に対して不足しています。説明に合わせて、カラム名を考え直してください。
- total(支払い合計)は「sell_detailsの購入価格カラム」を作成すれば計算可能なので不要
  - データベースの負荷を考えるとあったほうがよい
- sell_idのINDEXに○がない
  > 主キーであるsell_idはデフォルトでINDEXがつくため、INDEX欄に○を記載してください。 
## 指摘事項
## 全体
- PKがidになっていない(テーブル名_idとなっている。これだと@user.user_idみたいになる)

## users
- user_l_nameなど略語はよろしくないです。

## discs
- 外部キーとしてproduct_idは必要です。(1:多なので)

## sells
- totalを作成しないとリレーションで引っ張ってきたテーブルのカラムの合計値を計算しないといけないためデータベースに負荷がかかります(sell_detailsの価格✖️個数をeachで回すみたいな)
