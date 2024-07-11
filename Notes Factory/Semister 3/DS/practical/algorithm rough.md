```mermaid
flowchart TD
    A[Start] --> B[Input number of elements]
    B --> C[Declare array of size n]
    C --> D[Input elements of the array]
    D --> E[Print elements of the array]
    E --> F[Input element to search for]
    F --> G[For i = 0 to n-1]
    G --> H{Is arr[i] equal to search?}
    H -->|Yes| I[Print element found at index i]
    I --> J[Set found flag to 1]
    J --> K[End loop]
    K --> L{Is i equal to n-1?}
    L -->|No| G
    H -->|No| K
    L -->|Yes| M{Is found flag still 0?}
    M -->|Yes| N[Print element not found]
    M -->|No| O[End]
    N --> O
    K --> G
    O[End]