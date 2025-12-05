Edtech diagram

```mermaid
flowchart LR
    Student[Student] --> SF
    Teacher[Teacher] --> TF
    Admin[Admin] --> AF
    Parent[Parent] --> PF
    
    subgraph F[frontends]
        TF@{ shape: doc, label: "teacher dashboard"}
        SF@{ shape: doc, label: "student frontend"}
        AF@{ shape: doc, label: "Admin frontend"}
        PF@{ shape: doc, label: "Parent frontend"}
    end

    A[[Auth]]
    GW[[Gateway]]
    F -->  GW --> A
    GW --> CR & Comm & P

    CR[[classroom]] --> DB
    Comm[[Communication]] --> ES[[email-service]] 
    P[[profile]] --> DB
    DB[(DB)]
    
    
    