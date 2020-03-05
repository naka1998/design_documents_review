# テーブル定義書2

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を全体, 共通, などとしてください。

## 全体
- テーブル名は先頭大文字にする
- created_at, updated_atのデータ型がtimestampでなくdatetimeになっている
- 入荷を表すテーブルが存在しない

## admins
- admin_email, admin_passwordのadmin_は不要
- admin_idのINDEXに○がない
## users
- member_statusのデータ型がinteger/enumとあるのに、DEFAULTはfalse
 - 退会している OR していない、のはずなのでデータ型をbooleanにすべき
 - booleanにする場合、カラム名はis_hogehogeにするのがよい
- user_l_name, user_f_name, user_l_kana, user_f_kana, user_tel, user_email, user_passwordのuser_は不要

## ships
- ship_name, ship_address, ship_tel, ship_codeのship_は不要
- ship_idのINDEXに○がない
## products
- products_idが複数形になっている
- 「商品名」を表すカラム名をcd_titleとするのは不適
- 要件「在庫数は入荷記録と受注詳細記録から算出する」より、stockは不要
- 「stock_status(在庫ステータス)」を表すカラムは不要
 - 「販売ステータス」を表すカラムは必要
## discs
- products_idは不要
- disc_numのdisc_は不要
- disc_idのINDEXに○がない
## songs
- 曲名を格納するカラム名としてsongは不適(nameにすべき)
## labels
- レーベル名を格納するカラム名としてlabelは不適(nameにすべき)
## aritists
- アーティスト名を格納するカラム名としてartistは不適(nameにすべき)
## genres
- ジャンル名を格納するカラム名としてgenreは不適(nameにすべき)
## cart items
- テーブル名の単語区切りがスペースになっている
- Cart item_idはカラム名として不適(先頭大文字・単語区切りがスペース)。cart_item_idとすべき
- Cart item_idのINDEXに○がない
- products_idが複数形になっている
- buy numの「buy 」は不要
## sell_details
- sell_details_Idが複数形になっている、「I」が大文字になっている
- products_idが複数形になっている
- products_idのFKに○がない
- sell_numのsell_は不要
- FKとしてsell_idがない
- 「購入価格」を表すカラムがない
## sells
- sell_details_Idは不要
- 「支払い方法」を表すカラム名として、payでは「方法」を表せていない
- total(支払い合計)は「sell_detailsの購入価格カラム」を作成すれば計算可能なので不要
- sell_idのINDEXに○がない

## 指摘事項
## 全体
- PKがidになっていない(テーブル名_idとなっている。これだと@user.user_idみたいになる)

## users
- user_l_nameなど略語はよろしくないです。

## discs
- 外部キーとしてproduct_idは必要です。(1:多なので)

## sells
- totalを作成しないとリレーションで引っ張ってきたテーブルのカラムの合計値を計算しないといけないためデータベースに負荷がかかります(sell_detailsの価格✖️個数をeachで回すみたいな)
