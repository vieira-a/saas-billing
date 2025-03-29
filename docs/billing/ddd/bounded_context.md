```
graph TD
%% Definindo Bounded Contexts
A[Billing Context]
B[Payment Context]
C[Subscription Context]
D[Transaction Context]
E[User Management Context]

    %% Interactions
    A -- "Uses Payment" --> B
    A -- "Manages Subscriptions" --> C
    B -- "External Payment Provider" --> F[Payment Provider]
    C -- "Stores Subscription Data" --> E
    D -- "Records Transactions" --> B
    A -- "Records Transactions" --> D
    C -- "Manages Subscription" --> A
    E -- "User Information" --> A
    E -- "User Information" --> C

    %% Bounded Contexts representations
    class A,B,C,D,E circle
    classDef circle fill:#f9f,stroke:#333,stroke-width:2px;
```
