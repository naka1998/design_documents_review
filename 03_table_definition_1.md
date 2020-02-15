# テーブル定義書1

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。

## 全体
- 

## Admin
- テーブル名が単数形
- 「admin_id」のPKに○がない。
- 「admin_id」のAUTO INCREMENTALに○がない
- 「admin_id」のINDEXに○がない
## Users
- 「user_○_name」「user_○_kana」はそれぞれfirstとlastのことだと思われるが分かりづらい
- 「ship_address」とあるが、これだと配送先住所を1つしか持てない
- 「member_status」のデータ型がstringになっている
- 「user_f_name」「user_f_kana」のNOT NULLに○がない
## Products
- 「products_id」が複数形になっている
- 「disc_id」を持っている
- 「genre_id」「label_id」「artist_id」のFKに○がない
- テーブル名は「Products」なので「cd_image」「cd_title」のcd → productのほうがいい
- 「発売日」を格納するカラムがない
- 「cd_image」のDEFAULTが「画像準備中」になっている
- 「stock」がある(「在庫数は入荷記録と受注詳細記録から算出する」と異なる)
- 「stock_status(在庫ステータス)」はあるが「販売ステータス」がない
## Disks
- 「track_num」がある
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
- 「subtotal(小計金額)」は不必要
## Buy details
- 「buy_details_id」が複数形になっている
- 「buy_id」を持っていない
## Buy
- 「buy_details_id」を持っている
- 配送先郵便番号・配送先氏名を持っていない
- 「buy_at(購入日)」は不必要
- 「pay」のデータ型がstringだが、enum使うことを考えたらintegerか
