# テーブル定義書1

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。

## 全体
- created_at, updated_atの説明が全てユーザ登録日時・更新日時になっている
- created_at, updated_atのデータ型がtimestampでなく、datetimeになっている
## Admin
- テーブル名が単数形
- 「admin_id」のPKに○がない。
- 「admin_id」のAUTO INCREMENTALに○がない
- 「admin_id」のINDEXに○がない
- 「admin_email」「admin_password」の「admin_」が不要
## Users
- 「user_○_name」「user_○_kana」はそれぞれfirstとlastのことだと思われるが分かりづらい
- 「ship_address」とあるが、これだと配送先住所を1つしか持てない
- 「member_status」のデータ型がstringになっている
- 「member_status」だと意味が通りづらい。「is_active」などにすべき
- 「user_f_name」「user_f_kana」のNOT NULLに○がない
- 「user_l_name」「user_f_name」「user_l_kana」「user_f_kana」「user_tel」「user_email」「user_password」の「user_」が不要
- 「zip_code(郵便番号)」「user_tel(電話番号)」のデータ型がintegerになっている(stringにすべき)
## Products
- 「products_id」が複数形になっている
- 「disc_id」を持っている
- 「genre_id」「label_id」「artist_id」のFKに○がない
- 「cd_image」「cd_title」の「cd_」が不要
- 「発売日」を格納するカラムがない
- 「stock」がある(「在庫数は入荷記録と受注詳細記録から算出する」と異なる)ので削除する
- 「stock_status(在庫ステータス)」はあるが「販売ステータス」がない
- 「」
## Disks
- 「track_num」がある
- 「products_id」が複数形になっている
## Songs, Labels, Artists, Genreまとめて
- PKが存在しない
- 「曲名」や「レーベル名」を格納するカラムの名前が「song」「label」ではわかりづらい。
また、label以外はデータ型がintegerになっている
## Labels, Artists, Genresまとめて
- 「products_id」は必要ない
## Songs
- 「disc_id」のAUTO INCREMENTALに○がある
- ディスク内の曲順を管理するカラムが必要
## Genre
- テーブル名が単数形
## Cart item, Buy details
- テーブル名の単語の間をスペースで区切っている
- 「buy num」がスペース区切りになっている
## Cart item
- PKが存在しない
- テーブル名が単数形
- 「products_id」のデータ型がない
- 「products_id」が複数形になっている
- 「subtotal(小計金額)」は不必要
## Buy details
- 「buy_details_id」が複数形になっている
- 「buy_id」を持っていない
- テーブル名を管理者から見た名前にする(受注詳細を意味するOrder_detailsとか)
- テーブル名の変更に合わせて「buy_num(購入枚数)」も変更すべき
## Buy
- 「buy_details_id」を持っている
- 配送先郵便番号・配送先氏名を持っていない
- 「buy_at(購入日)」は不必要
- 「pay」のデータ型がstringだが、enum使うことを考えたらintegerか
- テーブル名を管理者から見た名前にする(受注を意味するOrdersとか)
- 「stock(支払合計)」では意味が一致しない。日本語に合わせたカラム名にする
- 「pay(支払い方法)」では意味が一致しない。「方法」を含むカラム名にする

**研修担当レビュー**
合格です
一応カラム名にテーブル〜系の指摘は全体でもしておくと良いです。(確認後このメッセージは削除して構いません。)
