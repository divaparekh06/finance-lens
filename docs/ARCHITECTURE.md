# Finance Lens — System Architecture

## 1. Architectural Overview

Finance Lens will follow a layered architecture that separates the application's user interface, business logic, and data access responsibilities.

The architecture is designed to improve maintainability, testability, and scalability while keeping the application manageable for a solo development project.

### Core Layers

1. **Presentation Layer** — Handles the user interface and user interactions using Flutter widgets.
2. **Business Logic Layer** — Handles financial calculations, analytics, validation rules, and generation of financial insights.
3. **Data Layer** — Handles authentication, data persistence, and communication with external services such as Firebase Authentication and Cloud Firestore.

The general flow of the application is:

Presentation Layer → Business Logic Layer → Data Layer




## 2. Data Layer

The Data Layer is responsible for managing the application's persistent data and communication with external services.

### Repository

Repositories provide the business logic layer with a consistent interface for accessing and modifying application data. Finance Lens will use repositories for major data entities such as Transactions, Budgets, and Categories.

Repositories abstract the details of data storage from the rest of the application.

### Services

Services handle communication with external technologies and platforms. Finance Lens will use services for technologies such as Firebase Authentication and Cloud Firestore.

The conceptual data flow is:

Presentation Layer → Business Logic → Repository → Service → Firebase




## 3. State Management

Finance Lens will use Riverpod for application state management.

State management will coordinate changing application data and ensure that relevant parts of the user interface respond to state changes.

State may include authentication status, transactions, budgets, selected filters, loading states, and error states.

Riverpod will also help manage dependencies between presentation components, business logic, and repositories while supporting testable application architecture.

The conceptual flow is:

User Interaction → State Management → Business Logic → Repository → Firebase

Changes in application state will propagate back to the relevant Flutter UI components.



## 4. Authentication and Authorization

Finance Lens will use Firebase Authentication to manage user registration, login, logout, and authenticated sessions.

Authentication determines the identity of a user, while authorization determines which application features and data the user is permitted to access.

Each authenticated user will be identified using the unique Firebase Authentication UID, which will also be used to associate the user's financial data with their account.

The initial application roles will be:

- **User** — Can manage their own transactions, budgets, categories, and financial analytics.
- **Admin** — Can perform limited administrative operations such as managing application-level configuration and predefined categories.

Access control will be implemented at both the application level and the Firestore security-rule level. UI-level restrictions will control the features presented to users, while Firestore security rules will provide the underlying data-access protection.

Users will only be permitted to access their own private financial records.



## 5. Navigation Architecture

Finance Lens will use a bottom navigation structure for its primary application areas.

### Primary Navigation

The primary navigation will contain four sections:

1. **Home** — Provides an overview of the user's financial status, including monthly spending, budget utilization, and recent transactions.
2. **Transactions** — Allows users to view, add, edit, and delete financial transactions.
3. **Analytics** — Provides visual and analytical insights into spending patterns, category-wise spending, and financial trends.
4. **Profile** — Allows users to view and manage their account and application preferences.

### Secondary Screens

The following screens will be accessed from the primary sections when required:

- Add Transaction
- Edit Transaction
- Transaction Details
- Budget

These screens will not appear as permanent items in the bottom navigation.

### Authentication Flow

When the application starts, the authentication state will be checked. Authenticated users will be directed to the main application, while unauthenticated users will be directed to the Login screen.

The primary navigation flow is:

Home ↔ Transactions ↔ Analytics ↔ Profile



## 6. Initial UI Wireframe

The initial interface will prioritize simplicity and quick access to the user's most important financial information.

### Home Screen

The Home screen will provide a concise overview of the user's financial activity.

It will contain:

- Monthly spending and budget utilization
- Quick access to add a transaction
- Recent transactions
- A summary financial insight
- Bottom navigation for the primary application sections

Conceptual layout:

    ┌───────────────────────────────┐
    │ Good morning 👋              │
    │                               │
    │ Monthly Spending              │
    │ ₹7,200 / ₹10,000              │
    │ ██████████████░░░░ 72%        │
    │                               │
    │       + Add Expense           │
    │                               │
    │ Recent Transactions            │
    │                               │
    │ Food                  ₹250    │
    │ Transport             ₹80     │
    │ Education             ₹150    │
    │                               │
    │ Financial Insight             │
    │ Spending analysis summary     │
    │                               │
    ├───────────────────────────────┤
    │ Home | Transactions | Analytics | Profile │
    └───────────────────────────────┘

### Empty States

The application will provide meaningful empty-state messages when the user has not yet created transactions, budgets, or other relevant data.

For example, a new user will be encouraged to add their first transaction rather than being presented with an empty or confusing dashboard.



## 7. Analytics Screen

The Analytics screen will transform stored financial data into meaningful summaries and visual insights.

### Analytics Components

The initial Analytics screen will contain:

1. **Spending Summary** — Displays total spending, current budget, and remaining budget for the selected period.
2. **Category Breakdown** — Displays category-wise spending using numerical summaries and a visual chart.
3. **Spending Trend** — Displays changes in spending over time using a suitable chart.
4. **Financial Insights** — Provides concise observations derived from the user's financial data.

Analytics will be calculated dynamically from transactions, budgets, and categories rather than stored as an independent database entity.

### Initial Insight Strategy

The first version of Finance Lens will use rule-based financial insights. Examples include identifying the highest spending category, detecting increases or decreases in spending, and warning users when budget utilization becomes high.

Machine-learning-based features such as spending prediction may be considered as an optional enhancement after the core application has been completed.



## 8. Transactions Screen

The Transactions screen will provide users with a centralized interface for managing their financial transactions.

### Core Operations

The screen will support the complete CRUD lifecycle:

- **Create** — Add a new financial transaction.
- **Read** — View existing transactions and transaction details.
- **Update** — Edit an existing transaction.
- **Delete** — Remove an existing transaction after confirmation.

### Transaction Fields

The initial transaction form will contain:

- Amount
- Description
- Category
- Date
- Payment method

### Transaction List

The transaction list will display recent transactions with relevant information such as description, category, date, and amount.

Users will be able to search and filter transactions to locate specific records.

### Transaction Details

Selecting a transaction will open a details view containing the complete transaction information and actions for editing or deleting the transaction.

### Empty State

When no transactions exist, the application will display a meaningful empty-state message and provide a direct option to add the user's first transaction.

Changes to transactions will be reflected in related budget calculations, analytics, and financial insights.



## 9. Budget Screen

The Budget screen will allow users to define and monitor a spending budget for a selected period.

The initial implementation will focus on a monthly budget.

The screen will display:

- Budget amount
- Total spending for the selected period
- Remaining budget
- Budget utilization percentage
- Visual progress indicator

Users will be able to create and update their budget.

Budget utilization will be calculated dynamically from the user's transactions.

The budget status may also be used by the financial insight system to generate relevant spending warnings.



## 10. Profile Screen

The Profile screen will provide basic account and application management features.

It will display the authenticated user's basic account information and provide access to:

- Account information
- Notification preferences
- Application settings
- About information
- Logout

The profile module will remain intentionally lightweight to keep the primary focus of Finance Lens on financial tracking and analytics.




## 11. Authentication Screens

Finance Lens will provide Login and Registration screens for user authentication.

### Login

The Login screen will allow users to authenticate using their registered email address and password.

### Registration

The Registration screen will allow new users to create an account using their name, email address, and password.

### Validation

Authentication forms will include input validation and basic error handling.

Examples include:

- Required-field validation
- Email format validation
- Password validation
- Password confirmation validation
- Authentication failure handling

After successful authentication, users will be directed to the main application.



                 FINANCE LENS
                      │
        ┌─────────────┴─────────────┐
        │                           │
 AUTHENTICATION                 MAIN APP
        │                           │
   ┌────┴────┐          ┌──────────┼───────────┐
   │         │          │          │           │
 Login    Register     Home   Transactions  Analytics
                              │
                         ┌────┼────┐
                         │    │    │
                        Add  Edit Delete

                           Home
                            │
                          Budget

                         Profile



# TECH STACK
| Component        | Technology                          |
| ---------------- | ----------------------------------- |
| Mobile framework | Flutter                             |
| Language         | Dart                                |
| State management | Riverpod                            |
| Authentication   | Firebase Authentication             |
| Database         | Cloud Firestore                     |
| Notifications    | Firebase Cloud Messaging            |
| Charts           | Flutter-compatible charting library |
| Version control  | Git                                 |
| Repository       | GitHub                              |
| IDE              | VS Code                             |

