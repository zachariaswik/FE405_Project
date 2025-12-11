Edtech diagram

```mermaid
flowchart LR
    classDef frontend fill:#7ed957,stroke:#333,stroke-width:1px,color:#000
    classDef services fill:#c084fc,stroke:#333,stroke-width:1px,color:#fff

    %% Users
    Student[Student] --> FE
    Teacher[Teacher] --> FE

    %% Single Frontend
    FE[Frontend App]:::frontend --> GW

    subgraph Client[Client Facing]
        FE
    end

    %% Gateway + Services
    subgraph Internal[Internal Services]
        GW[[API Gateway]]:::frontend --> AUTH
        AUTH[[Auth]]:::services --> UDB[(User Database)]:::services

        %% Auth returns role: student/teacher
        AUTH --> FE

        %% App routes requests to relevant services
        GW --> CRS[[Classroom Service]]:::services --> REP[[Reporting Service]]:::services & CDB & AUTH
        REP --> CDB[(Course Database)]:::services
    end

    %% Legend
    subgraph Legend
        direction LR
        F_X[Frontend Layer]:::frontend
        S_X[Service Layer]:::services
    end


    