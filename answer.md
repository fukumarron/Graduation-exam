### このファイルに回答のER図を貼り付けて提出してください

```mermaid

erDiagram
    USERS {
        string email PK "ユニーク、必須"
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
        int id PK
        string name
        string breed
        date birthdate
        string gender "enumを検討する（'Male', 'Female', 'Unknown'）"
        int user_id FK "ユーザーID"
    }
    WALK_RECORDS {
        int id PK
        string date
        string route "ユーザーが自由に散歩ルートの名前を入力できる"
        int duration "散歩にかかった時間（分単位）"
        string notes "散歩ルートの詳細メモ（実際の通過点など）"
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
        string category "enumを検討する（'Food', 'Medical', 'Grooming'など）"
        decimal amount
        string date
        string notes "支出の詳細メモ"
        int user_id FK "ユーザーID"
    }
    USERS ||--o{ DOGS : "has"
    USERS ||--o{ WALK_RECORDS : "logs"
    DOGS ||--o{ FOOD_RECORDS : "eats"
    USERS ||--o{ EXPENSE_RECORDS : "spends"

