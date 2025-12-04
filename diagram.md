Here is a simple flow chart:

```mermaid
flowchart LR
    Student[Student] --> SF
    Teacher[Teacher] --> TF
    API_GATEWAY['API Gateway]
    
    TF@{ shape: doc, label: "teacher dashboard"}
    SF@{ shape: doc, label: "student frontend"}

    SF -- API_GATEWAY
    API_GATEWAY--> TF

    Auth[auth]
    TF --> Auth
    SF --> Auth

    DB[(DB)]
    TF --> DB
    SF --> DB


```
