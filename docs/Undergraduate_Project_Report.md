# Undergraduate Software Project Report
## Design and Implementation of a Personal Income and Expense Tracking Application

**Student:** Doğan Bozkurt  
**University:** Selçuk University, Faculty of Technology, Computer Engineering  
**Degree:** B.Sc. Computer Engineering (graduated 14 June 2024)  
**Course 1:** Engineering Design (*Mühendislik Tasarımı*), code 3301654, semester 6, 6 ECTS  
**Course 2:** Computer Engineering Applications (*Bilgisayar Mühendisliği Uygulamaları*), code 3301751, semester 7, 4 ECTS  
**Source code:** [ExpenseTrackerFinalProject](https://github.com/DoganBozkurt/ExpenseTrackerFinalProject)  
**Document status:** English-language reconstruction prepared in November 2026

## Summary

This project began as a course assignment in which I had to choose an engineering problem, research possible solutions and explain how I intended to build a working system. I chose to develop a web application for keeping track of personal income and expenses. The idea was to make it easier to enter transactions, group them under categories and see a clear summary of the recorded figures without repeatedly calculating totals by hand.

The work continued across two undergraduate courses. During Engineering Design, I selected the topic, discussed it with my academic advisers, researched how the application could be organised, prepared a plan, and presented both a report and a demonstration. During Computer Engineering Applications, I focused on implementing the application and presenting the working output and results. The completed codebase uses ASP.NET Core MVC, Entity Framework Core and SQL Server. It includes account registration and login, category and transaction management, and a dashboard with charts.

### About this document

I no longer have the original reports and presentation files that I submitted for these courses; they appear to have been lost when my computer was reformatted. I have therefore written this English account in 2026 from what I remember of the coursework, together with the source code and two application screenshots that I still have. It is a reconstruction of the work, **not** a copy of the original Turkish submissions or a newly certified university report.

## 1. Engineering Design: choosing the topic and preparing the project

The first stage took place in Engineering Design (semester 6, 6 ECTS). My initial task was to find a suitable project topic. I wanted to work on a software problem that could be turned into an actual application, rather than stopping at an idea or a design diagram. A personal income and expense tracker gave me a manageable problem with several connected parts: users, transactions, categories, a database and a way of displaying results.

After deciding on the topic, I discussed the idea with academic staff and sought their feedback before proceeding. Once the topic was accepted, I researched possible approaches and thought about the main functions the application would need. I planned how a user would add an income or expense record, associate it with a category, and later review the information on a dashboard. I also considered how the data and application logic should be organised so that the different parts would not be mixed together.

This stage was not only about writing code. It involved explaining the problem, preparing the proposed solution, considering the steps needed to build it and documenting that work. I prepared a report, presented it as part of the course and showed a demonstration of the project approach. The original report and demonstration material are no longer available, so I cannot reproduce exactly what was shown at that time. What I can document now is the purpose of the work and how the later implementation followed the same project topic.

## 2. Computer Engineering Applications: turning the plan into a program

The following course, Computer Engineering Applications (semester 7, 4 ECTS), was the practical continuation of the project. Instead of focusing mainly on the topic and design, I worked on building the application, connecting the database and checking the output of the different screens. The main deliverable was a working web application, with the results shown through its pages and financial summaries.

I implemented the project as an ASP.NET Core MVC application. I used C# for the application logic, Entity Framework Core for database access and SQL Server for storing the records. The work was divided into separate projects for the web interface, business logic, data access and entities. This helped me keep the transaction calculations, database operations and user interface in their own places while developing the system.

By the end of the practical stage, the application provided a transaction list and a dashboard that calculated income, expenses and balance from stored records. It also displayed expenses by category and a visual comparison of income and expenses. Two surviving screenshots show these outputs. I presented the implementation and its results as the outcome of the second course.

### How these courses relate to the official curriculum

The university's Bologna descriptions explain the intended progression: Engineering Design covers defining a problem, developing and evaluating solutions, and documenting and communicating the design process; Computer Engineering Applications focuses on applying computer engineering knowledge to design, implement, verify, report and present a realistic engineering solution. My recollection of the two project stages is consistent with those course objectives.

## 3. What I built

### Application structure

The repository contains four main C# projects:

| Project | Purpose |
|---|---|
| `MVCProject` | MVC controllers, Razor views, transaction and dashboard screens |
| `BusinessLayer` | Transaction/category managers and FluentValidation rules |
| `DataAccesesLayer` | Entity Framework Core, repository operations and SQL Server context |
| `EntityLayer` | User, role, transaction, category, icon and contact models |

The available source code targets **.NET 7**.

### Using the application

A registered user can sign in and work with their own transaction and category lists. The application contains pages for adding, editing and deleting income or expense records. Each transaction has a category, amount, date and note. Form validation checks basic inputs, including whether an amount is greater than zero. Categories have their own management pages, and administrative functions are restricted by user roles.

For the dashboard, the code retrieves transactions belonging to the signed-in user for a recent **seven-day period**. It totals income and expenses separately, calculates the difference as the balance and groups expense records by category. The interface presents these values as summary cards, a doughnut chart and an income-versus-expense line chart. The application also displays recent transactions in a table. I used Syncfusion components for several of these tables and charts.

### Supporting components

The project uses ASP.NET Core Identity for user authentication and role management. FluentValidation provides rules for forms such as registration, categories and transactions. Serilog is configured to write application logs, and a middleware component handles unexpected errors.

The repository also contains code for checking email format and a ZeroBounce API method, but the API call is commented out in the available version; I therefore do **not** describe live ZeroBounce verification as a completed feature.

The software project is internally named `MVCProject` because it uses the Model–View–Controller pattern. This is a technical project name, **not** the name of a separate university course.

## 4. Screenshots and visible results

Two screenshots of the earlier application interface survived. The first shows the **dashboard** with income, expenses, balance and category-based charts. The second shows the **transaction list** with categories, dates, amounts and edit/delete actions.

The screenshots are preserved by the applicant and reproduced in the separate five-page PDF version of this report. They are not embedded in this GitHub text edition. Dates and amounts in those screenshots represent application records, not evidence of the exact coursework submission date.

## 5. Results and what I learned

The project resulted in a web application that brings financial records into one interface. Based on the surviving code and screenshots, the application includes the main functions I set out to build: users can maintain transaction records, organise them into categories and view financial summaries. The interface makes these summaries easier to understand than a plain list of numbers. A particular result of the work was seeing the same database records used in different ways: as editable transactions, calculated totals and chart data.

The two stages were useful in different ways. The first taught me to move from an idea to an approved and documented engineering plan, including discussions with instructors and a presentation of the proposed work. The second gave me experience with implementation decisions and the practical difficulties of connecting a user interface, application rules and a database. Looking back at the code, I can also see choices that I would improve in a newer version, particularly handling configuration secrets outside the repository, strengthening the handling of permissions and passwords, and adding automated tests.

This is a software development project, **not an experimental study**. I do not claim that it was evaluated using a formal user study, performance benchmark or security audit. The original graded reports and feedback are missing, and the repository does not prove precisely which source-code changes were completed during each individual semester. My description of the course activities is based on my recollection; the implementation details are supported by the surviving code and screenshots.

## 6. Supporting university records

The official Selçuk University Diploma Supplement, section **4.2**, states that the Computer Engineering curriculum includes a research project and a final project among the programme's graduation requirements. The separate Bologna course descriptions identify Engineering Design as a **6-ECTS** face-to-face undergraduate module (code **3301654**, semester 6) and Computer Engineering Applications as a **4-ECTS** face-to-face undergraduate module (code **3301751**, semester 7). The two descriptions set out the educational objectives of design/documentation and implementation/verification respectively.

My account is that I worked on this **same software project** across those two modules, which together carry **10 ECTS**. I am not claiming that Selçuk University officially awarded a single 10-ECTS thesis. Whether these two modules meet another university's specific requirement for independent academic work is a decision for that university.

### Evidence and references

1. Selçuk University Diploma Supplement, section 4.2 and course table in section 4.3 (official document provided separately with the university application).
2. Engineering Design and Computer Engineering Applications Bologna course descriptions (original language: Turkish; supplied by the applicant).
3. [Project source code](https://github.com/DoganBozkurt/ExpenseTrackerFinalProject).
4. Two surviving application screenshots (provided separately in the five-page PDF version).

---

*Doğan Bozkurt · English-language reconstruction prepared in November 2026. Not an official university-issued report.*
