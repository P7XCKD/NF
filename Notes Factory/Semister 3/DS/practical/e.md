ee
```mermaid
flowchart TD
    A[Start] --> B[Input n]
    B --> C[Declare array]
    C --> D[Input arr elements]
    D --> E[Print arr elements]
    E --> F[Input search element]
    F --> G{For each element in arr}
    G --> H{Is element equal to search?}
    H -->|Yes| I[Print found at index]
    I --> J[Set found]
    J --> K[End loop]
    K --> L{Is last element?}
    L -->|No| G
    H -->|No| K
    L -->|Yes| M{Is found?}
    M -->|No| O[End]
    M -->|Yes| N[Print not found]
    N --> O
    O[End]