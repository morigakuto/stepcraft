```mermaid
erDiagram
    USERS ||--|{ TASKS : "creates"
    USERS ||--o{ GROUP_MEMBERS : "belongs to"
    TASKS ||--|{ SUB_TASKS : "is divided into"
    GROUPS ||--|{ GROUP_MEMBERS : "has"
    TASKS ||--o{ TASK_TAGS : "has"
    TAGS ||--o{ TASK_TAGS : "is attached to"

    USERS {
        int id
        string email
        string password_hash
        string nickname
        string icon_url
        string goal
        string user_type
        date created_at
        date updated_at
    }

    TASKS {
        int id
        int user_id
        string title
        string status
        date created_at
        date updated_at
    }

    SUB_TASKS {
        int id
        int task_id
        string title
        string status
        date completed_at
        date created_at
        date updated_at
    }

    GROUPS {
        int id
        string name
        string goal_category
        date created_at
        date updated_at
    }

    GROUP_MEMBERS {
        int group_id
        int user_id
        bool is_bot
        date joined_at
    }

    TASK_TAGS {
        int task_id
        int tag_id
    }

    TAGS {
        int id
        string name
    }
```

#### 各テーブルの概要

| テーブル名 | 概要 |
|------------|------|
| USERS | ユーザー情報を管理。 |
| TASKS | ユーザーが入力した大元のタスクを管理。 |
| SUB_TASKS | AIによって細分化された具体的なステップを管理。 |
| GROUPS | 共通の目標を持つユーザーが所属するグループ。 |
| GROUP_MEMBERS | ユーザーとグループの関連を管理する中間テーブル。AIボットもここで。 |
| TAGS / TASK_TAGS | タスクのカテゴリ分け用。達成記録の可視化などに利用。 |

#### 画面一覧
- サインアップ/ログイン画面
- オンボーディング画面 (初回利用時のプロフィール・目標設定)
- ホーム画面 (タスク管理)
- グループ画面
- マイページ画面 (達成記録)
- 設定画面

