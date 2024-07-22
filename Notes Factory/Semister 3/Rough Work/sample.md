```mermaid
erDiagram
    STUDENT {
        studentid
        first_name
        last_name
        birth_date
        email
    }
    
    COURSE {
        course_id PK
        course_name
        credits
        department_id FK
    }
    
    DEPARTMENT {
        department_id PK
        department_name
    }
    
    ENROLLMENT {
        enrollment_id PK
        student_id FK
        course_id FK
        enrollment_date
        grade
    }
    
    STUDENT ||--o{ ENROLLMENT : enrolls
    COURSE ||--o{ ENROLLMENT : includes
    DEPARTMENT ||--o| COURSE : offers
    ```