# Book a Doc Web Application

## Tables of Contents

1. [Introduction](#introduction)  
2. [Entity Relationship Diagram ](#entity-relationship-diagram)  
    - [Entities, Relationships, and Foreign Keys](#entities-relationships-foreign-keys)  
3. [Features and Functions](#features-and-functions)  
4. [Programming Paradigm](#programming-paradigm)  
    - [Imperative programming](#imperative-programming)  
        - [Procedural programming](#procedural-programming)  
        - [Object oriented programming](#object-oriented-programming)
    - [Declarative programming](#declarative-programming)  
        - [Functional programming](#functional-programming)    
        - [Logic programming](#logic-programming)  
5. [Software Architecture Pattern](#software-architecture-pattern)  
    - [Layer Architecture](#layer-architecture)
    - [Model View Controller](#model-view-controller) 
    - [Event Driven Architecture ](#event-driven-architecture) 
6. [Project Management Methodology](#project-management-methodology)  
    - [Agile](#agile)  
    - [Kanban](#kanban)  
7. [Task Management Methodology](#task-management-methodology)    
8. [Client/Server Architecture Fundamentals and Implementation](#client/server-architecture-fundamentals-and-implemention)   
    - [Client/Server Communication](#client/server-communication)   
    - [Data Distribution](#data-distribution) 
    - [Data Security](#data-security)   
    - [Feature Distribution](#feature-distribution)    
    - [Authorisation and Authentication](#authorisation-and-athentication) 
    - [Validation](#validation) 
9. [User Stories for Book A Doc](#user-stories-for-book-a-doc)  
10. [Ethical Principles](#ethical-principles)    
    - [Privacy and Data Protection](#privacy-and-data-protection)   
    - [Security and Data Integrity](#security-and-data-security)     
    - [Transparency](#transparency)   
    - [Fairness and Non-Discrimination](#fairness-and-non-discrimination)   
11. [References](#references)  

## Introduction

My Book A Doc system is designed to make booking GP appointments quick and easy. Patients can sign up or login to book and manage their appointments.   
The application allows patients to search available doctors and medical centres without having an account. However, if the patient wishes to make a booking, upon clicking the book button the system will direct the patient to either sign up or sign in to continue with the booking.

## Features and Functions

- Sign up & Login:  
    - Patients can create an account to book and manage their appointments. 

- Search for Doctors and Medical Centres: 
    - Users can find GPs based on specialty, availability, and medical centre location. 

- Appointment Booking: 
    - Logged in patients can select a doctor, choose a time, and book instantly. 

- Appointment Management: 
    - Patients can view their upcoming appointments with the option to cancel and past appointments, along with the appointment status (confirmed, completed, or cancelled).

- Medical Centre Details: 
    - Displays Doctor’s name, specialties, medical centre, availability, and booking button. 

## Programming Paradigm

![Programming Paradigm Diagram](images/programming_paradigm.png)

A programming paradigm is a way of thinking about and structuring code. It’s a set of principles, patterns, and styles that guide how developers write and organise programs.
Different paradigms influence how developers solve problems, structure data, and manage the flow of logic in the application.  
There are two types of programming paradigm:  

1. **Imperative programming:** code is written as a sequence of instructions that changes the program's state step by step  
- **Procedural programming:**  
    - organised into procedures or functions that manipulate data for reusability
- **Object oriented programming:**   
    - organised around objects that contain data and code. Uses:  
        - Encapsulation: bundle data and methods that operate on that data    
        - Inheritance: create new classes based on existing ones  
        - Polymorphism: same interface but different implementations  
        - Abstraction: hide complex implementation details  
2. **Declarative programming:** describes what needs to be done and focuses on the output or result
- **Functional programming** Uses:
    - Pure functions: same input will always produce the same output  
    - Immutable: the data can not be changed once created
    - First class functions: the functions can be passed as arguments
    - Higher order functions: functions that can operate on other functions  
- **Logic programming:** set if principles that are based on facts and rules  

Since my Book A Doc application involves handling user requests, managing data, and ensuring smooth functionality. 
I will use a mix of paradigms:  
- **Imperative Programming** for step by step processes like authentication an database transactions
- **Procedural Programming** for structuring routes and handling requests in Express.js   

```bash
// validating input and checking Dr availability
function createBooking(req, res) {
    const { patientId, doctorId, date } = req.body;
}
```
- **Object oriented Programming** for managing patients, doctors and bookings using Mongoose models   

```bash
// define schemas and models to represent Patient entity
const Patient = new mongoose.Schema ({
    name: String,
    dateOfBirth: Date
    email: String
    password: String    
})
```
- **Declarative Programming** for MongoDB queries

```bash
Doctor.find({ specialty: "Women's Health", available: true });
```
- **Functional Programming** for writing reusable utility functions

```bash
// formatting dates
const formatDate = (date) => newDate(date).isISOString() .split("T")[0]
```

## Software Architecture Pattern

![Software Architecture Patterns Diagram](images/software_architecture_patterns.png)

A software architecture pattern is a general structure or blueprint that defines how components of an application interact with each other.  
It provides a framework for organising an application's codebase, and helps developers organise code in a way that is scalable, maintainable, efficient.  
Common architectural patterns:  

- **Monolithic Architecture** a single tightly integrated codebase    
- **Layered (N-Tier) Architecture** separates an application into logical layers    
- **Model View Controller** separates concerns into Models, Views and Controllers  
- **Microservices Architecture** divides the application into small, independent services    
- **Event Driven Architecture** components communicate by triggering an responding to events  
- **Serverless Architecture** uses cloud-base functions instead of managing servers    

My Book A Doc system will follow the layer architecture, model view controller and event driven architecture.

### Layer Architecture

![Layered Architecture Diagram](images/layered_architecture.png)

A layered architecture separate an application into different layers, each handling a specific part of the system. 
In my application, I will have:

- Presentation Layer (Frontend in the future)  
    - handles user interaction (UI)  
    - displays available doctors, medical centres, and bookings   

```bash
// route/bookingRoutes.js
const express = require("express");
const router = express.Router();
const bookingController = require("../controllers/bookingController");

// Create a new booking
router.post("/", bookingController.createBooking);

// Get all bookings
router.get("/", bookingController.getBookings);

module.exports = router;
```  

- Application Layer (Express.js API)   
    - process user requests such as login and book an appointment  
    - ensure business logic is executed correctly  
- Data Layer (MongoDB)  
    - manages the database  
    - stores patients, doctors and bookings   

### Model View Controller (MVC)

[MVC Diagram](images/mvc_pattern.png)

I will structure my Express.js using the MVC pattern:  
- Model  
    - handles database interaction using Mongoose models. For example, Patient, Doctor, and Booking models define data structures
- View  
    - all the UI logic of the application. For example, text box, search bar, book button, etc   
- Controller
    - manages request handling and business logic. For example bookingController.js would process booking requests, checks doctors availability, and saves appointments     

### Event Driven Architecture   

![Event Driven Diagram](images/event_driven.png)

I will use event driven architecture to handle and respond to API requests:  

```bash
// handles booking when patient submits a booking request
app.post("/bookings", (req, res) => {})
```

## Project Management Methodology

[Project Management Methodology Diagram](images/project_management_methodology.png)

A project management methodology is a structured framework that guides the planning, execution, and completion of a project.   
It defines the processes, roles, and workflows for teams to follow to ensure efficiency, collaboration, and successful delivery.  
Common project management methodologies:    

- **Waterfall** a linear, step by step approach where each phase must be completed before moving to the next  
- **Agile** a flexible, iterative approach that encourages collaboration and adapting to change  
- **Scrum** a framework under Agile that organises work into short cycle sprints
- **Kanban** a visual workflow method that manages work using a board with tasks at different stages
- **Lean** a methodology focused on minimising waste and maximising value    

Since my Book A Doc system is a solo project, I need a methodology that allows flexibility while keeping progress structured.   
To manage this project I will apply the agile and kanban methodology.   

### Agile

![Agile Methodology Diagram](images/agile.png)

Agile focuses on continuous development and improvement, making it a good fit for a coding project where requirements might evolve.  
I will use the following agile principles:  

- **Iterative Development** building the system in small, testable parts instead of all at once     
- **Frequent Testing** continuously testing component like user authentication and booking logic  
- **Feedback Driven Improvements** adjusting based on testing results or feedback from my peers  

For example, instead of completing the entire system before testing, I would:  
1. develop user authentication - test and refine  
2. add booking functionality - test again before moving to the next feature  
3. improve based on feedback  

### Kanban

![Kanban Methodology Diagram](images/kanban.png)

A kanban board is a simple and effective way to manage tasks. It consists of columns representing different stages of work.     
Each task moves from left to right as your work progresses. The visual layout helps to identify bottlenecks and ensure tasks are completed efficiently.    
To keep track of my progress, I will use the kanban methodology to organise tasks into visual categories like:  

- To Do - eg. set up database models 
- In Progress  - eg. plan and design documentation
- Completed  - eg. ERD   

## Task Management Methodology  

![Trello Diagram](images/trello.png)

A task management methodology is a structured approach to planning, organising, tracking, and completing tasks efficiently. It ensures tasks are prioritised, dependencies are managed, and work is completed within deadlines.  

Task management is crucial in software development, where multiple tasks, like writing code, testing, debugging, and deploying need to be handled systematically. By following  a structures methodology, developers can break down large projects into manageable pieces, track progress, and ensure timely completion.  

I will be using Trello to manage tasks for my Book A Doc system, I can take advantage of its kanban style board, which allows me to visually track
progress, and prioritise tasks. Each task will be created as a Trello card that I can move across these columns as work progresses. For example:

![Trello Card Diagram](images/trello_card.png)

## Client/Server Architecture Fundamentals and Implementation  

![Client Server Architecture Diagram.](images/client_server_architecture.png)

Client/server architecture is computing model in which multiple clients (users or devices) communicate with a server (central system) over a network. The server provides services like processing requests, storing data, and managing authentication, while the client handles user interactions.  

This architecture is widely used in web applications, mobile apples, and cloud-based platforms. My Book A Doc system follows this model, where a frontend client communicates with the backend server (Node.js, Express.js, MongDB).  

### Client/Server Communication

![Client Server Communication Diagram](images/client_server_communication.png)

Client and server communication happens using HTTP or HTTPS request via RESTful APIs or WebSockets. 
In my Book A Doc application, the client (user interface) will send requests to the server to:

- fetch available doctors and medical centres
- book an appointment
- authenticate user through sign up, login and logout

An example of client request to book an appointment:  

```bash
async function bookAppointment() 
    const response = await fetch("/api/bookings", {
        method: "POST",
        headers: {
            "Content-Type": "application/json"
        },
        body: JSON.stringify ({
            patientId: "17",
            doctorId: "5",
            date: "2025-02-10"
        })
    });
```

An example of the server response:  

```bash
{
    "message": "Confirmed",
    "booking": {
        "patient": 17,
        "doctor": 5,
        "date": ""2025-02-10
    }
}
```

### Data Distribution

![Date Distribution Diagram](images/data_distribution.png)

In client/server architecture, data can be stored and processed in different ways to optimise performance and security:  

1. **centralised storage:** data is stored on the server like MongoDB    
2. **cached Data:** frequently accessed data like doctor lists is cached to improve performance    
3. **client side storage:** the client may store small amounts of data like authentication tokens in local storage  

How my Book A Doc system will handle data distribution:  

- patient, doctor, and booking data is stored in MongoDB on the server  
- session tokens for logged-in users are stored on the client local storage. For example, when a user searches for doctors, the frontend may cache results so that repeated searches load faster  
- cached API responses can be used for static data like list of specialties for doctors. For example, when a user logs in, their session token is stored in local storage for authentication    


### Data Security

Data security protects confidential information from the unauthorised access, theft, or corruption.  
How my Book A Doc system ensure data security:  

- **encryption:** passwords are hashed with bcrypt before storage
- **HTTPS communication:** all API calls use HTTPS to encrypt data in transit
- **role-based access control (RBAC):** patients cannot access other user's booking
- **cross origin resource sharing (CORS):** controls which clients have access my API
- **data security:** sensitive fields such as passwords are never stored in plain text

An example of password hashing with bcrypt.js  

```bash
const bcrypt = require("bcrypt");

const hashPassword = async (password) => {
    const salt = await bcrypt.genSlat(10);
    return await bcrypt.hash(password, salt);
};
```  

### Feature Distribution

![Feature Distribution Diagram](images/feature_distribution.png)    
 
Feature distribution refers to which tasks are handled by the client vs the server.    
How my Book A Doc system will distribute features:    

- **Client-side Frontend** UI display, basic validation, sending requests  
- **Server-side Backend** database operations, authentication, business logic  

![Book A Doc Feature Distribution Diagram](images/my_feature_distribution.png)  

### Authorisation and Authentication  

![Authentication Diagram](images/authentication.png)  

Authorisation and authentication ensure secure access control:

- **Authorisation:** verifies who a user is through login with email and password
- **Authentication:** determines what a user can do. For example in my Book A Doc system, only a logged in patient can book an appointment.

How my Book A doc system will handle authorisation and authentication: 

1. **user logs in:** sends credentials to /api/auth/login
2. **server verifies credentials:** if correct, it issues a JWT token
3. **user accesses protected routes:** the client includes the JWT token is future requests
4. **server verifies token:** if valid, it allows access

A code example:  

```bash
const jwt = require("jsonwebtoken")

const User = require("../models/user")

const checkIfAdmin = async (req, res, next) => {
    let token = req.get("authorization") // Bearer the-actual-token
    token = token?.split(" ")?.[1] // the-actual-token
    if (!token) {
        return res.status(401).json({ error: "Unauthenticated" })
    }
    try {
        const payload = jwt.verify(token, "secret")
        const user = await User.findById(payload.id)
        if (!user.is_admin) {
            throw new Error()
        }
        req.userId = payload.id
        next()
    } catch(err) {
        console.log(err)
        return res.status(401).json({ error: "Unauthenticated / not an admin" })
    }
}

module.exports = checkIfAdmin
```

### Validation  

![Validation Diagram](images/validation.png)    

Validation ensures data integrity and security by preventing incorrect or malicious input. It occurs on both the client and server.   

- Client-side Validation:
    - checks basic input before sending data to the server, eg. email format
    - improves user experience by providing instant feedback. For example:  

```bash
function validateEmail(email) {
    return email.includes("@") ? true : "Invalid email format";
}
```
- Server-side Validation:  
    - ensures data meets strict requirements before being stored    
    - prevents security vulnerabilities like     

How my Book A doc system uses validation:    

- **client-side validation** for instant feedback eg. highlighting incorrect form fields    
- **server-side validation** for security & data integrity eg. ensuring valid doctor IDs in booking  

## User Stories for Book A Doc

1. Patient user stories: 

- **feature:** user sign up and login
    - as a patient, I want to create an account so that I can book and manage my appointments securely  
    - **justification:** only registered users should be able to book appointments, ensuring patient information is stored securely  

 - **feature:** search for Doctors and Medical Centres
    - as a patient, I want to search for doctors by specialty and location so that I can find a suitable GP near me  
    - **justification:** patients need a convenient way to find doctors that fit their needs without manually browsing through an entire list 

- **feature:** booking an appointment  
    - as a patient, I want to select an available time slot for a doctor so that I can schedule an appointment that fits my schedule    
    - **reason:** I want flexibility in choosing a time that fits into my schedule    

- **feature:** appointment management
    - as a patient, I want to view, reschedule, or cancel my appointments so that I can manage my healthcare easily  
    - **reason:** I don't want to have to call to cancel or reschedule 
   
2. Doctor user stories: 
Doctors use the system to manage their schedules and view patients appointments

- **feature:** managing availability    
    - as a doctor, I want to update my availability so that patients can only book appointments when I am free    
    - **reason:** I need to control my schedule to avoid double bookings   

- **feature:** viewing my schedule  
    - as a doctor, I want to see my upcoming appointments so that I can prepare for my patient in advance  
    - **reason:** I just need a quick overview of my schedules  

- **feature:** managing appointments  
    - as a doctor, I want to approve or decline appointment requests so that I can ensure availability before confirming bookings  
    - **justification:** Doctors may have emergencies or last minute schedule changes and need control over their appointments  

- **feature:** patient contact information  
    - as a doctor, I want to view a patient's contact details so that i can reach out if necessary   
    - **justification:** Doctors may need to contact patients for follow ups or appointment changes     

3. Admin user stories:  
Admins oversee the platform, ensuring smooth operations and handling user management, security, and system monitoring  

- **feature:** user management  
    - as an admin, I want to manage patient and doctor accounts so that I can ensure system security and remove inactive users    
    - **justification:** the system needs administrative control to prevent unauthorised access and manage users  

- **feature:** overseeing appointments
    - as an admin, I want to monitor all booked appointments so that I can resolve disputes or system issues  
    - **justification:** admins need visibility into booking in case of patient complaints or system failures  

- **feature:** monitoring system performance
    - as an admin, I want to track server uptime and errors so that I can quickly fix technical issues  
    - **reason:** I don't want users to experience downtime, so I need to catch issues early

- **feature:** ensuring data security
    - as an admin, I want to enforce security policies and restrict access so that patient data remains confidential  
    - **reason:** the system has sensitive medical information, and proper security measures are necessary to comply with privacy laws  

## Ethical Principles

For my Book A Doc application, the ethical principles I will adhere to, and the tools/systems I will use to ensure they are implemented correctly are below:

### Privacy and Data Protection

My Book A Doc application handles personal information like names, emails, date of birth, addresses etc, I will ensure that user data is kept private and secure by:  

- only collecting necessary information: I won't ask users for unnecessary details  
- secure user passwords: passwords will be hashed before storage using bcrypt.js, so they are never stored in plain text  
- secure user authentication: users will log in with a JWT token stored in HTTP only cookies to prevent unauthorised access  
- allow users to delete their account: if a patient no longer wants an account, they should be able to request deletion  

Tools and implementation:  
- bcrypt.js: to hash and securely store passwords  
- HTTPS encryption: ensures data is securely transmitted over the internet  
- MongoDB Atlas Security: protects stored data from unauthorised access  

The privacy policy page will explain what data is collected, how it's used, and how users can request account deletion.  

### Security and Data Integrity

Since users will be booking appointments and managing personal details, I need to make sure the system is secure and that only authorised users can access their own data by:  

- role-base access control (RBAC): patients can only manage their own appointments, and doctor can only see their own schedule    
- limit login attempts: I will use Express Rate Limit to block too many failed attempts    
- regular data backups: in case of system failure, backups will prevent data loss    

Tools and implementation:    
- JSON web token (JWT): secures user authentication  
- express validator: prevents bad input from being processed  
- helmet.js: adds security to HTTP headers  
- Express Rate Limit: blocks excessive failed login attempts  

The terms and conditions page will include basic security guidelines for users eg, "do share you login details with anyone"  


### Transparency

Users should know what to expect when using my Book A doc application. I will ensure transparency by:    

- clear messaging in the UI: users will get confirmation messages for actions like bookings or cancellations  
- no hidden terms: the system will clearly state how it works and what users agree to when signing up  
- contact option for any questions or concernsL if users have issues, they should have an easy way to get help  

Tools and implementations:  
- privacy policy and terms & conditions pages: explaining everything in simple language
- contact us page: allowing users to ask question or report issues  

### Fairness and Non-Discrimination

My Book A Doc system will be fair for all users, ensuring equal access to services without bias or unfair restrictions by:  

- equal access for all: the system will not prioritse certain users over others when booking appointments  
- no special privileges for doctors: doctors cannot manipulate bookings to block patients unfairly  
- consistent booking rules: the same rules will apply to all users, preventing any unfair advantages  
- clear cancellation and rescheduling policies: so patients and doctors know their rights if they need to cancel or change a booking  

Tools and implementations:  
- first come, first serve booking system: all will be available to all users equally  
- audit logs: to track suspicious booking patterns  

The terms and conditions page will clearly outline fair booking policies and cancellation rules.

## References

ByteByteGo (2023). Top 5 Most Used Architecture Patterns. [online] YouTube. Available at: https://www.youtube.com/watch?v=f6zXyq4VPP8 [Accessed 18 Oct. 2024].

Design ✨, T.M. (2023). The Art of Ethical Website Design: Creating a Positive Impact Online. [online] TMDesign. Available at: https://medium.com/theymakedesign/ethical-website-design-ee4bec179e28.

DEV Community. (n.d.). Introduction to Programming - What is Programming Paradigm? [online] Available at: https://dev.to/dchhitarka/introduction-to-programming-what-is-programming-paradigm-3le1.

Edraw Team (2019). Trello Flowcharts – An Effective Approach To Streamline Teamwork. [online] EdrawMax. Available at: https://edrawmax.wondershare.com/flowchart/trello-flowchart.html [Accessed 8 Feb. 2025].

Edstem.org. (2025). Ed Discussion. [online] Available at: https://edstem.org/au/courses/20401/lessons/69467/slides/463542 [Accessed 9 Feb. 2025].

Gautam, S. (n.d.). Client-Server Model or Architecture. [online] www.enjoyalgorithms.com. Available at: https://www.enjoyalgorithms.com/blog/client-Server-architecture.

GeeksforGeeks (2019). Client-Server Model - GeeksforGeeks. [online] GeeksforGeeks. Available at: https://www.geeksforgeeks.org/client-server-model/.

GeeksforGeeks (2024). Client-Server Architecture System Design. [online] GeeksforGeeks. Available at: https://www.geeksforgeeks.org/client-server-architecture-system-design/.

geeksforgeeks (2020). Introduction of Object Oriented Programming. [online] GeeksforGeeks. Available at: https://www.geeksforgeeks.org/introduction-of-object-oriented-programming/.

geeksforgeeks (2021). Types of Software Architecture Patterns. [online] GeeksforGeeks. Available at: https://www.geeksforgeeks.org/types-of-software-architecture-patterns/.

GeeksforGeeks. (2020). Difference between Client /Server and Distributed DBMS. [online] Available at: https://www.geeksforgeeks.org/difference-between-client-server-and-distributed-dbms/.

Gurnov, A. (2024). What is Agile Methodology in Project Management? [online] Wrike. Available at: https://www.wrike.com/project-management-guide/faq/what-is-agile-methodology-in-project-management/.

Healey, Anthony.M. (2019). Differentiate between client-side and server-side validations in Web pages. [online] www.ttmind.com. Available at: https://www.ttmind.com/techpost/Differentiate-between-client-side-and-server-side-validations-in-Web-pages.

Matthews, B. (2025). Top 5 Types of Project Management Methodologies. [online] TechnologyAdvice. Available at: https://technologyadvice.com/blog/project-management/project-management-methodologies/.

Misic, N. (2024). 12 Ethical Principles In Web Design: A Comprehensive Guide. [online] cliowebsites.com. Available at: https://cliowebsites.com/ethical-principles-in-web-design/.

Radigan, D. (2024). What is kanban? [online] Atlassian. Available at: https://www.atlassian.com/agile/kanban.

Shahed C (2019). Validation in ASP .NET Core. [online] Wake Up And Code! Available at: https://wakeupandcode.com/validation-in-asp-net-core/ [Accessed 9 Feb. 2025].

Shaibu, S. (2024). Introduction to Programming Paradigms. [online] Datacamp.com. Available at: https://www.datacamp.com/blog/introduction-to-programming-paradigms.

Terra, J. (2022). What is Client-Server Architecture? Everything You Should Know | Simplilearn. [online] Simplilearn.com. Available at: https://www.simplilearn.com/what-is-client-server-architecture-article.

Tharindu Piyumal (2022). Difference between event-driven and command line programming. [online] Medium. Available at: https://piyumalt.medium.com/difference-between-event-driven-and-command-line-programming-d3b25da94242.

tutorialspoint (2019). MVC Framework - Introduction - Tutorialspoint. [online] Tutorialspoint.com. Available at: https://www.tutorialspoint.com/mvc_framework/mvc_framework_introduction.htm.

vswami11 (2020). Develop internal IT project management methodologies. [online] PMWithVee. Available at: https://epmtutorial.wordpress.com/2020/01/22/develop-internal-it-project-management-methodologies/.

Warren Wilansky , Stephanie Beasse (2021). The Principles of Ethical Web Design. [online] capacity-interactive. Available at: https://capacityinteractive.com/blog/the-principles-of-ethical-web-design/.

World, J. (2022). Programming Paradigms | Functional Programming | Object Oriented Programming | Logic | java world. [online] www.youtube.com. Available at: https://www.youtube.com/watch?v=ySBTM-FKEtg [Accessed 4 Feb. 2024].

