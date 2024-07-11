e

```mermaid
graph LR
    subgraph Input
        A[User enters number of elements (n)] --> B{Array creation (arr[n])}
        B --> C{User enters elements of the array}
    end

    subgraph Processing
        C --> D{Iterate through each element (i = 0 to n-1)}
            D --> E[Compare current element (arr[i]) with search element]
                E --> F{Element found (found = 1)}
                F --> G{"Element %d found at index %d" }
                E --> H{Element not found}
                H --> I{"Search continues"}
            D --> I
    end

    I --> J(Loop ends)

    subgraph Output
        J --> K{Print search result}
    end

    A --> B
    J --> K
    ```