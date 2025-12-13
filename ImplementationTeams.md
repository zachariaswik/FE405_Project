# ImplementationTeams

To start working on my MVP, I would initially start with one team, consisting of one tech lead and 3 developers.

* Tech lead, DevOps
    * Auth and Gateway. Handles gateway config, auth service. Sets up the UserDB to handle authetication specific user Data. CI/CD pipelines. 

* Frontend Developer
    * Develops the teach/student frontends. 

* Backend Developer A
    * Develops ClassroomService. Creates the logic behind the core classroom fuctions.

* Backend Developer B 
    * Develops reportingService and classroomDB. Handles the logic of dataflow from ClassroomService down to reportingService, and classroomDB. 


At this stage, there would be a lot of communication needed between the developers. Therefore, it would be much more efficient for everyone to work in the same team.


### Moving to Phase 1

In phase 1, I would expand to three separate teams: Frontend, Backend, and Security/Quality - with a total of 9 devs. 

The frontend would have three devs owning the three separate frontends for Admin, Teacher and Student. It is important that within the frontend team, they work together to align their frontend design. 
The person in charge of the Admin frontend, will be the team lead and also main responsible for consistency and core functionality.

* Frontend(3)
    * Teacher frontend(1)
    * Student frontend(1)
    * Admin frontend / team lead(1)


The backend team would consist of 4 devs. One for each service which directly communicates with the frontend, and two devs on the reportingService/ClassroomDB/MQ services. I would have the teamlead, being more senior, working on the MQ; as this service has a higher risk when in production. 

* Backend(4)
    * ClassRoomService (1)
    * CourseService (1)
    * ReportingService/ClassroomDB/MQ
        - reportinService + MQ / Teamlead (1)
        - reportinService + classroomDB(1)

Finally, I would have two people dealing with Security and Quality. We also have the tech lead in this team, who owns the whole product.

* Security/Quality team
    * UserDB & auth (1)
    * Gateway & Techlead (1)
