# Finance Lens — Project Scope

## 1. Project Overview

Finance Lens is a cross-platform mobile application designed to help users record, organize, and analyze their personal spending.

The application will provide transaction management, budgeting, financial analytics, and data-driven financial insights through a simple and user-friendly mobile interface.

The project will be developed as an individual semester project using Flutter and Firebase, with a primary focus on delivering a practical, maintainable, and deployable minimum viable product.

## 2. Problem Statement

Managing personal finances requires users to keep track of their spending, organize transactions, maintain budgets, and understand changes in their financial behavior.

However, simply recording individual expenses does not provide meaningful insight into overall spending patterns. Users may find it difficult to identify their major spending categories, monitor budget utilization, compare spending across periods, and recognize changes in their financial behavior.

Finance Lens aims to address this problem by combining transaction tracking, budgeting, analytics, and data-driven financial insights within a single mobile application.

## 3. Project Objectives

The primary objectives of Finance Lens are:

1. To provide secure user authentication and account management.
2. To enable users to create, view, update, and delete personal financial transactions.
3. To allow users to define and monitor monthly spending budgets.
4. To present spending information through meaningful summaries, charts, and trends.
5. To generate rule-based financial insights from the user's transaction and budget data.
6. To provide a simple, responsive, and user-friendly cross-platform mobile interface.
7. To securely store and manage application data using Firebase Authentication and Cloud Firestore.
8. To implement appropriate input validation, error handling, testing, and documentation.
9. To produce a deployable application suitable for beta testing and submission through the appropriate application distribution platform.


## 4. Core MVP Scope

The following capabilities are considered essential for the first complete version of Finance Lens.

### Authentication

- User registration
- User login and logout
- Authentication state management
- Input validation
- Basic authentication error handling

### Transaction Management

The application will provide complete CRUD functionality for financial transactions:

- Create transactions
- View transactions
- View transaction details
- Update transactions
- Delete transactions

### Categories

- Predefined spending categories
- Assign categories to transactions
- Category-wise spending analysis

### Budget Management

- Create a monthly budget
- Update the budget
- View budget utilization
- Calculate remaining budget

### Dashboard

The dashboard will provide:

- Total monthly spending
- Budget utilization
- Recent transactions
- Basic financial insights
- Quick access to add a transaction

### Analytics

The application will provide:

- Total spending summaries
- Category-wise spending analysis
- Spending trends
- Budget comparison
- Rule-based financial insights

### Notifications

The application will support relevant notifications such as budget-related alerts and application updates using Firebase Cloud Messaging.

### Quality, Documentation and Deployment

The project will include:

- Input validation
- Basic error handling
- Unit and widget testing for key modules
- GitHub repository and documentation
- Release APK/AAB generation
- Beta testing
- Appropriate application-store or institute-account deployment

## 5. Future Enhancements

The following features may be considered after the core MVP has been completed and stabilized:

- Machine-learning-based spending prediction
- Advanced spending pattern analysis
- More personalized financial insights
- Additional interactive visualizations
- Smarter personalized notifications

Future enhancements will not be allowed to delay or compromise completion of the core MVP.

## 6. Out of Scope

The following capabilities are outside the initial scope of Finance Lens:

- Direct bank-account integration
- Real-money transactions
- Payment processing
- Stock trading
- Investment portfolio management
- Cryptocurrency management
- Loan management
- Tax filing or tax management
- Credit-score management
- Financial-account aggregation
- Professional financial advice
- Complex accounting and bookkeeping
- Social networking between users

Finance Lens will focus on personal financial tracking, budgeting, analytics, and data-driven insights rather than functioning as a banking, payment, investment, or accounting platform.


## 7. Technology Stack

Finance Lens will use the following technologies and tools:

| Component | Technology |
|---|---|
| Mobile Framework | Flutter |
| Programming Language | Dart |
| State Management | Riverpod |
| Authentication | Firebase Authentication |
| Database | Cloud Firestore |
| Push Notifications | Firebase Cloud Messaging |
| Data Visualization | Flutter-compatible charting library |
| Testing | Flutter Unit and Widget Testing |
| Version Control | Git |
| Repository Hosting | GitHub |
| Primary Deployment Target | Android |
| Distribution | Google Play Store / Institute Developer Account |

The technology stack is selected to support cross-platform development while keeping the implementation manageable for an individual semester project.

Specific third-party packages will be selected during implementation based on project requirements, compatibility, maintenance status, and simplicity.

## 8. Feature and Requirement Matrix

The following matrix maps the major project requirements to their planned implementation in Finance Lens.

| Requirement | Priority | Planned Implementation |
|---|---|---|
| User Authentication | Must Have | Firebase Authentication |
| Role-Based Access | Must Have | User/Admin authorization model |
| Transaction CRUD | Must Have | Flutter UI + Cloud Firestore |
| Budget Management | Must Have | Flutter UI + Cloud Firestore |
| Category Management | Must Have | Application logic + Firestore |
| Dashboard | Must Have | Flutter + Riverpod |
| Financial Analytics | Must Have | Derived transaction and budget data |
| Financial Insights | Must Have | Rule-based business logic |
| Responsive UI | Must Have | Flutter responsive layouts |
| Firebase Integration | Must Have | Firebase Authentication + Cloud Firestore |
| Push Notifications | Must Have | Firebase Cloud Messaging |
| Input Validation | Must Have | Flutter form validation |
| Error Handling | Must Have | UI and service-layer handling |
| GitHub Repository | Must Have | Git + GitHub |
| Project Documentation | Must Have | Markdown documentation + IEEE-format SRS |
| Unit Testing | Must Have | Flutter unit tests |
| Widget Testing | Must Have | Flutter widget tests |
| Release Build | Must Have | Android APK/AAB |
| Deployment | Must Have | Google Play Store / appropriate institute account |
| ML-Based Prediction | Optional | Future enhancement |
| Advanced Analytics | Optional | Future enhancement |

### Requirement Traceability

The project will prioritize completion of all Must Have requirements before implementing optional enhancements. Optional features will only be considered after the core application has been implemented, tested, and stabilized.