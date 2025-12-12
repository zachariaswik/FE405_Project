 Reporting generates student activity statistics
    - Reporting | assessmentDB

```mermaid
sequenceDiagram
    ClassroomService ->>+ ReportingService: generateStudentStats
    ReportingService ->>+ ClassroomDB: getStudentData
    ClassroomDB ->>- ReportingService: studentData
    ReportingService ->> ReportingService: computeStats
    ReportingService ->>+ ClassroomDB: writeStudentStats
    ClassroomDB ->>- ReportingService: Success
    ReportingService ->>- ClassroomService: Success
```