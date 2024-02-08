### このファイルに回答のER図を貼り付けて提出してください

```mermaid

erDiagram
    USERS ||--o{ DOGS : "飼っている"
    DOGS ||--o{ WALK_RECORDS : "散歩を記録"
    DOGS ||--o{ FOOD_RECORDS : "食べ物を記録"
    USERS ||--o{ EXPENSE_RECORDS : "支出を記録"
    USERS {
        string email "ユニーク、必須"
        string encrypted_password "必須"
        string reset_password_token "ユニーク"
        datetime reset_password_sent_at
        datetime remember_created_at
        integer sign_in_count "デフォルトは0"
        datetime current_sign_in_at
        datetime last_sign_in_at
        string current_sign_in_ip
        string last_sign_in_ip
        string name "以前のusernameをnameに変更"
    }
    DOGS {
        int id PK "犬のID"
        string name "名前"
        string breed "犬種"
        date birthdate "誕生日"
        string gender "性別(enum: 'Male', 'Female', 'Unknown')"
        int user_id FK "ユーザーID"
    }
    WALK_RECORDS {
        int id PK
        date walk_date "散歩日"
        string route "ルート名"
        int duration "散歩時間(分)"
        string notes "散歩の詳細メモ"
        int dog_id FK "犬のID"
    }
    FOOD_RECORDS {
        int id PK
        string food_type "フードの種類（市販フード、手作り食など）"
        string description "フードの詳細説明（材料、重量など）"
        int dog_id FK "犬のID"
    }
    EXPENSE_RECORDS {
        int id PK
        string category "支出のカテゴリ(enum: 'Food', 'Medical', 'Grooming'など)"
        decimal amount "金額"
        date expense_date "支出日"
        string notes "支出の詳細メモ"
        int user_id FK "ユーザーID"
    }
