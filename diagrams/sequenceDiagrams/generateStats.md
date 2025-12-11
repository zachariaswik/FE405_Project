 Reporting generates student activity statistics
    - Reporting | assessmentDB

```mermaid
sequenceDiagram
    ClassroomService ->>+ ReportingService: generateStudentStats
    ReportingService ->>+ ClassroomDB: getStudentData
    ClassroomDB ->>- ReportingService: returnStudentData
    ReportingService ->>+ ClassroomDB: writeStudentStats
    ClassroomDB ->>- ReportingService: Success
    ReportingService ->>- ClassroomService: Success
```


Question:
1. There is some algorithm running in ReportingService - SHOULD I show this, or should I add another layer saying something like "StatsComputing" like below.


```mermaid
sequenceDiagram
    ClassroomService ->>+ ReportingService: generateStudentStats
    ReportingService ->>+ ClassroomDB: getStudentData
    ClassroomDB ->>- ReportingService: studentData
    ReportingService ->>+ ComputeStats: studentData
    ComputeStats ->>- ReportingService: studentStats
    ReportingService ->>+ ClassroomDB: writeStudentStats
    ClassroomDB ->>- ReportingService: Success
    ReportingService ->>- ClassroomService: Success
```