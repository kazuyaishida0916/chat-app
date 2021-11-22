# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user


①トピックブランチ（マスターのコピー）を作成する
②トピックブランチ上で作業を進める
③作業に区切りがついたらコミット
④プッシュ

③と④を繰り返して一つの機能を完成させる

⑤プルリクエストを作成してレビューを受ける
⑥マージ
⑦プル

マスター            トピックブランチ（フロント実装）
                      コミット１
                      コミット２
                      コミット３
                      コミット４
          ＜＝マージ

履歴
コミット１
コミット２
コミット３
コミット４
フロント実装ブランチをマージしました




マスター            トピックブランチ１    トピックブランチ２  トピックブランチ３  トピックブランチ４
                    コミット１
        ＜＝マージ
                                      コミット２
        ＜＝マージ

コミット１
トピックブランチ１をマージしました
コミット２
トピックブランチ２をマージしました
コミット３
トピックブランチ３をマージしました
コミット４
トピックブランチ４をマージしました