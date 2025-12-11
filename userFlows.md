***User Flows***

1. Student login vs Teacher login.
    - student client | auth
    - teach client | auth
2. Teacher post question
    - Teacher client | classroomService

3. Student answer question.
    - student client  | ClassroomService

4. Teacher adds result to student.
    - Teacher client | classRoomService | reporting | AssessmentDB
5. Teacher open classroom.
    - Teacher client | classroomService
6. Student Joins classroom.
    - Student client | Auth | classroomService | userDB

8. Reporting generates student activity statistics
    - Reporting | assessmentDB

9. Teacher fetches student statistics
    - Teacher client | classroom | reporting | assessmentDB

