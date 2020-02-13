# 1. User Stories

* **As a patient, I want a system to pay my bills so that I don't have to pay in person.**
  * Priority: Should
  * Estimate: 7

* **As a doctor, I want to be able to pull up my patients' info so that I don't have to keep physical notes.**
  * Priority: Should
  * Estimate: 5

* **As a patient, I want to schedule my visits online so I don't have to call to schedule.**
  * Priority: Could
  * Estimate: 5

* **As a patient, I want to view the doctors working at the hospital so I can research them before scheduling a visit.**
  * Priority: Could
  * Estimate: 3


# 2. Use Cases

* **Pay a Bill**
  * Participating Actor(s): The patient.
  * Preconditions: The patient exists in the database and has at least one bill to pay.
  * Postconditions: The patient now has one less bill to pay.
  * Basic Event Flow:
    1. Patient logs into their account.
    2. Patient is authenticated.
    3. Patient navigates into the pay_bills screen.
    4. Patient clicks on the bill that they wish to pay.
    5. Patient enters credit card information.
    6. Patient clicks "Submit payment" button.
    7. Email Patient a receipt.
    8. Show Patient the receipt and alert them of the sent email.
  * Alternative Event Flows:
    * The Patient's credit card information could be invalid, in which case they will need to complete step 5 again.

* **View Patient Info**
  * Participating Actor(s): The doctor.
  * Preconditions: The doctor must exist in the database and have at least one patient.
  * Postconditions: The doctor is viewing one of their patient's information.
  * Basic Event Flow:
    1. Doctor logs into their account.
    2. Doctor is authenticated.
    3. Doctor navigates into the view_patients screen.
    4. Display a list of the doctor's patients.
    5. Doctor clicks on one of the patients.
    6. Display the patient's information.

* **Schedule Visit**
  * Participating Actor(s): The Patient.
  * Preconditions: The patient must have an account.
  * Postconditions: The patient will have a scheduled visit with a doctor.
  * Basic Event Flow: 
    1. Patient logs into their account.
    2. Patient is authenticated.
    3. Patient goes to the schedule_visit page.
    4. Use Outlook API to retrieve the patient's doctor's calendar.
    5. Display available times to the patient.
    6. The patient selects the time that works best for them.
    7. Ask the patient for confirmation.
    8. Add the visit to the doctor's calendar.
    9. Email the doctor about the newly-scheduled visit.
    10. Schedule a reminder email for the patient two days before the visit.
    11. Alert the user that the visit was successfully scheduled.
  * Alternative Event Flows: 
    * The Outlook API could fail.  In that case, return to step 4.
    * The email API could fail.  In that case, repeat the email request 3 times, then give an error and return to step 6.
    * There could be a race condition while scheduling.  In that case, give the first patient (based on timestamp) the visit time.  Return the other patient(s) to step 4 and display an error.

* **View Doctors**
  * Participating Actor(s): The patient.
  * Preconditions: None.
  * Postconditions: The patient will be able to view a list of doctors at the hospital.
  * Basic Event Flow: 
    1. The patient goes to the view_doctors screen.
    2. Show the patient a list of doctors.

# 3. UML Use Case Diagrams

**Pay a Bill**   
!["Pay a Bill" Use Case Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/UseCase_PayABill.png?raw=true)

**View Patients**   
!["View Patients" Use Case Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/UseCase_ViewPatients.png?raw=true)

**Schedule Visit**   
!["Schedule Visit" Use Case Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/UseCase_ScheduleVisit.png?raw=true)

**View Doctors**   
!["View Doctors" Use Case Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/UseCase_ViewDoctors.png?raw=true)
   

# 4. UML Class Diagrams

**Pay a Bill**   
!["Pay a Bill" Class Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/ClassDiagram_PayABill.png?raw=true)

**View Patients**   
!["View Patients" Class Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/ClassDiagram_ViewPatients.png?raw=true)

**Schedule Visit**   
!["Schedule Visit" Class Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/ClassDiagram_ScheduleVisit.png?raw=true)

**View Doctors**   
!["View Doctors" Class Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/ClassDiagram_ViewDoctors.png?raw=true)

# 5. UML Component Diagram

![Component Diagram](https://github.com/Hades948/SoftwareArchitectureHomework1/blob/master/ComponentDiagram.png?raw=true)