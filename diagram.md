Edtech diagram

```mermaid
flowchart LR
    Student[Student] --> SF
    Parent[Parent] --> PF
    Teacher[Teacher] --> TF
    Admin[Admin] --> AF
    
    
    subgraph F[client facing]
        TF@{ shape: doc, label: "teacher"}
        SF@{ shape: doc, label: "student"}
        PF@{ shape: doc, label: "Parent"}
        AF@{ shape: doc, label: "Admin"}
    end

    F -->  GW --> A
    subgraph B[internal]
        P_DB[(User
        Database)]

        A[[Auth]] --> P_DB
        GW[[Gateway]]    
        Ass[[TestService]] --> R
        GW --> CR & Comm & P & Course & Ass
        CR[[classroomService]] --> R
        Course[[CourseService]] --> R --> DB
        Comm[[MessagingService]]
        P[[UserAccount]] --> P_DB
        R[[Reporting]] 
        DB[(Assessment 
        Database)]

        R --> MQ[[ Message Queue]]
    end

    MQ --> Notifications

```

    
    

Questions:

* When is it worth separating the databases (Does it make sense to separate database for user profiles & Course related subjects)?

* 
    