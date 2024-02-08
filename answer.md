### このファイルに回答のER図を貼り付けて提出してください

```mermaid

erDiagram
    USER ||--o{ DOG : has
    USER {
        string username
        string email
        string password
    }
    DOG {
        string name
        string breed
        date birthday
        string gender
    }
    USER ||--o{ FEEDING-RECORD : logs
    FEEDING-RECORD {
        date date
        float quantity
    }
    USER ||--o{ HEALTH-RECORD : records
    HEALTH-RECORD {
        date date
        float weight
        int sleepHours
    }
    USER ||--o{ WALK-RECORD : tracks
    WALK-RECORD {
        date date
        string route
        int duration
    }
    DOG ||--o{ BOWL : uses
    BOWL {
        string size
        string material
    }
    USER ||--o{ EXPENSE-RECORD : notes
    EXPENSE-RECORD {
        string category
        float amount
        date date
    }
