# Library Database Entity Relationship Diagram

```mermaid
erDiagram
    USERS {
        int user_id PK
        int role_id FK
        varchar first_name
        varchar last_name
        varchar email
        varchar phone_number
        text address
        date date_of_birth
        date membership_date
        date membership_expiry
        varchar username
        varchar password_hash
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    USER_ROLES {
        int role_id PK
        varchar role_name
        text description
    }
    
    BOOKS {
        int book_id PK
        varchar isbn
        varchar title
        varchar subtitle
        int publisher_id FK
        date publication_date
        int category_id FK
        varchar language
        int page_count
        text description
        varchar cover_image_url
        timestamp created_at
        timestamp updated_at
    }
    
    AUTHORS {
        int author_id PK
        varchar first_name
        varchar last_name
        date date_of_birth
        date date_of_death
        text biography
        varchar nationality
    }
    
    BOOK_AUTHORS {
        int book_id PK,FK
        int author_id PK,FK
    }
    
    PUBLISHERS {
        int publisher_id PK
        varchar publisher_name
        text address
        varchar phone_number
        varchar email
        varchar website
    }
    
    CATEGORIES {
        int category_id PK
        varchar category_name
        text description
    }
    
    BOOK_COPIES {
        int copy_id PK
        int book_id FK
        varchar copy_number
        date acquisition_date
        numeric price
        varchar condition
        varchar location
        varchar status
        text notes
        timestamp created_at
        timestamp updated_at
    }
    
    BOOK_LOANS {
        int loan_id PK
        int copy_id FK
        int user_id FK
        date checkout_date
        date due_date
        date return_date
        int renewed_count
        numeric fine_amount
        boolean fine_paid
        int librarian_id FK
        text notes
        timestamp created_at
        timestamp updated_at
    }
    
    BOOK_RETURNS {
        int return_id PK
        int loan_id FK
        date return_date
        varchar condition_on_return
        int librarian_id FK
        numeric fine_assessed
        text notes
        timestamp created_at
    }
    
    USERS ||--o{ BOOK_LOANS : "borrows"
    USERS ||--o{ BOOK_LOANS : "processes as librarian"
    USERS ||--o{ BOOK_RETURNS : "processes as librarian"
    USER_ROLES ||--o{ USERS : "has role"
    
    BOOKS ||--o{ BOOK_COPIES : "has copies"
    BOOK_COPIES ||--o{ BOOK_LOANS : "is loaned"
    
    BOOK_LOANS ||--o{ BOOK_RETURNS : "is returned"
    
    PUBLISHERS ||--o{ BOOKS : "publishes"
    CATEGORIES ||--o{ BOOKS : "categorizes"
    
    BOOKS ||--o{ BOOK_AUTHORS : "written by"
    AUTHORS ||--o{ BOOK_AUTHORS : "writes"
```

## Database Schema Overview

This Entity Relationship Diagram (ERD) represents the Library Management System database structure. The database is designed to manage all aspects of a library, including:

1. **User Management**
   - User accounts with roles (librarian, member)
   - Membership tracking

2. **Book Catalog**
   - Books with detailed metadata
   - Authors and publishers information
   - Categories/genres

3. **Inventory Management**
   - Individual book copies with condition and location
   - Acquisition tracking

4. **Circulation**
   - Book loans and returns
   - Due date tracking
   - Fine assessment

### Key Relationships

- Books can have multiple authors (many-to-many relationship through BOOK_AUTHORS)
- Each book can have multiple physical copies (one-to-many)
- Users can check out book copies (one-to-many)
- Librarians (who are also users) can process loans and returns
- Books belong to categories and publishers (many-to-one)

This schema supports all essential library operations including cataloging, circulation, and user management.
