# Phase 1


***student frontend***
  - Class page
  - Authorization:
      * Limited read/write on course.

***Teacher frontend***
  - Class page
  - Authorization:
    * Reading/Writing rights to their owned courses.
    * Reading rights to all courses.


***Admin frontend***
  - Profile pages
  - Class pages
  - Authorization:
    * Read/Write rights to all courses.
    * Read/Write rights to all profiles.


Edtech diagram

```mermaid
flowchart LR
    classDef frontend fill:green
    classDef auth fill:blue
    classDef services fill:purple
    Student[Student] --> F
    Teacher[Teacher] --> F
    Admin[Admin] --> F
    
    
  subgraph F[client facing]
    direction RL
    TF:::frontend@{ shape: doc, label: "teacher"}
    SF:::frontend@{ shape: doc, label: "student"}
    AF:::frontend@{ shape: doc, label: "Admin"}
  end

  F -->  GW --> A --> F
  subgraph B[internal]
      P_DB[(User
      Database)]:::auth

      A[[Auth]]:::auth --> P_DB
      GW[[Gateway]]:::auth    
      GW --> CR & Course
      CR[[classroomService]]:::services --> R
      Course[[CourseService]]:::services --> R --> DB
      R[[Reporting]]:::services
      DB[(Assessment 
      Database)]:::services

      R --> MQ[[ Message Queue]]:::services
  end

    MQ --> Notifications


    %% Legend
    subgraph legend
        direction LR
        X[frontend]:::frontend
        Y[auth]:::auth
        Z[services]:::services
    end
```






