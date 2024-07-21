```mermaid
erDiagram
    STUDENT {
        int StudentID PK
        string FirstName
        string LastName
        date DateOfBirth
        string Email "multiple"
        int Age "derived"
    }

    COURSE {
        int CourseID PK
        string Title
        int Credits
    }

    ENROLLMENT {
        int EnrollmentID PK
        string Grade
        int StudentID FK
        int CourseID FK
    }

    STUDENT ||--o{ ENROLLMENT : "Enrolls"
    COURSE ||--o{ ENROLLMENT : "Enrolls"
    STUDENT ||--|| ENROLLMENT : "EnrollmentDetails"
    COURSE ||--|| ENROLLMENT : "EnrollmentDetails"
    ```