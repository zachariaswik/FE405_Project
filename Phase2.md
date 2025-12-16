# Phase 2

***Pupil frontend***
  - Their own profile page
  - Class page
  - Communication options with teacher and other pupils.
  - Collaboration space w. teacher/pupils
  - Authorization:
      * Limited view to only see enrolled courses
      * Limited read/write on course. 
      * Limited writing rights on their profiles

***Teacher frontend***
  - Their own profile page
  - Class page
  - Communication options with teachers, pupils and parents.
  - Collaboration space w. teacher/pupils
  - authentication with password and name
  - Authorization:
    * Reading/Writing rights to their owned courses.
    * Reading rights to all courses.
    * Read/Write on their profiles.


***Admin frontend***
  - Profile pages
  - Class pages
  - authentication with password and name
  - Authorization:
    * Read/Write rights to all courses.
    * Read/Write rights to all profiles.

*** Parent frontend ***
  - Children's profile page
  - Limited class page
  - Communication options with teachers.
  - authentication with password and name
  - Authorization:
    * Read-only profile.
    * communicaton only to teachers. 




Edtech diagram

```mermaid
flowchart LR
    classDef frontend fill:green
    classDef auth fill:blue
    classDef services fill:purple
    Student[Student] --> F
    Parent[Parent] --> F
    Teacher[Teacher] --> F
    Admin[Admin] --> F
    
    
  subgraph F[client facing]
    direction RL
    TF:::frontend@{ shape: doc, label: "teacher"}
    SF:::frontend@{ shape: doc, label: "student"}
    PF:::frontend@{ shape: doc, label: "Parent"}
    AF:::frontend@{ shape: doc, label: "Admin"}
  end

  F -->  GW --> A --> F
  subgraph B[internal]
      P_DB[(User
      Database)]:::auth

      A[[Auth]]:::auth --> P_DB
      GW[[Gateway]]:::auth    
      Ass[[Test Service]]:::services --> R
      GW --> CR & Comm & P & Course & Ass
      CR[[classroom Service]]:::services --> R
      Course[[Course Service]]:::services --> R --> DB
      Comm[[Messaging Service]]:::services
      P[[User Account]]:::auth --> P_DB
      R[[Reporting Service]]:::services 
      DB[(Course 
      Database)]:::services

      R --> MQ[[ Message Queue]]:::services & P_DB
  end
    MQ --> Notifications

    subgraph MicroService External Services
        MQ:::services
        MQ --> ES[[Email Service]]
        MQ --> Notifications
        
    end

    %% Legend
    subgraph legend
        direction LR
        X[frontend]:::frontend
        Y[auth]:::auth
        Z[services]:::services
    end
```

    











