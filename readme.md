```mermaid
erDiagram
    USERS ||--o{ ORDERS : places
    USERS ||--o{ REVIEWS : writes
    USERS ||--o{ CART_ITEMS : adds
    ORDERS ||--|{ ORDER_ITEMS : contains
    BOOKS ||--o{ ORDER_ITEMS : included_in
    BOOKS ||--o{ REVIEWS : reviewed_in
    BOOKS ||--o{ CART_ITEMS : added_to
    BOOKS ||--o{ BOOK_CATEGORIES : categorized_as
    CATEGORIES ||--o{ BOOK_CATEGORIES : groups
    AUTHORS ||--o{ BOOKS : writes

    USERS {
        int id PK
        string name
        string email
        string password
        string address
    }

    ORDERS {
        int id PK
        int user_id FK
        date order_date
        string status
        float total_amount
    }

    ORDER_ITEMS {
        int id PK
        int order_id FK
        int book_id FK
        int quantity
        float price
    }

    BOOKS {
        int id PK
        int author_id FK
        string title
        string description
        float price
        int stock_quantity
        string cover_image
    }

    REVIEWS {
        int id PK
        int user_id FK
        int book_id FK
        int rating
        string comment
        date review_date
    }

    CART_ITEMS {
        int id PK
        int user_id FK
        int book_id FK
        int quantity
    }

    CATEGORIES {
        int id PK
        string name
    }

    BOOK_CATEGORIES {
        int book_id FK
        int category_id FK
    }

    AUTHORS {
        int id PK
        string name
        string bio
    }
