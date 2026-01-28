# Football Victoria Referee Management Platform

This project is a full-stack web application (Python/DjangoREST + React) for managing referee appointments and availability for Football Victoria. The Football Victoria Referees department aims to provide a better experience for referees when appointing them to soccer matches by improving their current process with automation and convenience oriented design. This platform adds graphical visualisation to the existing Referees Appointment System.

### Note: This is a fork of the main project originally made for implementing CI/CD. This fork has the README abridged to solely cover my messaging functionality for portfolio presentation purposes. 

## SMS Messaging Sub-System

- The purpose of the SMS Sub-System is to streamline the process of offering appointments to referee's and enabling them to accept or decline them via SMS.
- The SMS Sub-System also automates the process of finding a new referee to oversee a given soccer match if the original referee declined the match.
- The automated re-assignment functionality pulls the referees who live near to the venue from the database, and offers it to them one by one until one accepts.
- By default, SMS messages offering match appointments are generated automatically when a match is created, and scheduled to be sent at 3:00pm on Monday afternoons.
- A 4 character phrase is generated for each match and must be sent back in the response, this security measure ensures referees can only cancel or confirm their own appointments.
- The 4 character phrases are bound to the phone number of the referee the match has been offered to, and is unbound then re-bound to a new referee's phone number if the original
  referee the match was offered to cancels. 


## SMS Scheduling
![sms-scheduling](./project-documents/resources/images/SMS-scheduling.png)
### Demo: Referee is offered and accepts a match appointment. 
https://github.com/user-attachments/assets/349c5b9e-0719-43ba-aae1-5b9fc2476406

- This clip shows the referee accepting the appointment and what this interaction between the user (referee) and the application looks like.
- The appointment is offered to the referee, presents the details of the match (time, date, skill division, location), as well as the 4 character security phrase.
- The referee responds by accepting the appointment, and sending the security phrase back to the application to confirm the appointment. 




## Appointment Re-assignnment
![automated-referee-replacement.png](./project-documents/resources/images/automated-referee-replacement.png)
### Demo: Referee is offered and delines match appointment, match is automatically re-assigned. 
https://github.com/user-attachments/assets/bd7e7cc7-8f75-401c-8857-0682b2bfb4d0


- This clip shows a couple of referees declining the match, and the match re-assignment logic in action.
- If the original referee declines, the application automatically calls the cloud database to fetch all referees who live near to the venue (determined by postcode).
- The application will offer the match to these referees one by one automatically until one accepts.
- Note: In this clip, the demo referees all possess my phone number for demo purposes so that I could demonstrate the match being offered to multiple referees. You'll notice the name of the referees change which reflects that in the backend, these messages are being sent to different referees within the system. 

