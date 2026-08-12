# Finance Lens — Data Model

## 1. User

The User represents an authenticated individual who uses Finance Lens to manage and analyze their personal financial data.

### Attributes

| Attribute | Description |
|---|---|
| `uid` | Unique identifier provided by Firebase Authentication |
| `name` | Display name of the user |
| `email` | Email address associated with the user's account |
|`role` | Authorization role assigned to the user, such as user or admin |

### Purpose

The User entity establishes ownership of the user's transactions, budgets, and other personal financial information.


## 2. Transaction

The Transaction represents an individual financial record created by a user.

### Attributes

| Attribute | Description |
|---|---|
| `id` | Unique identifier for the transaction |
| `userId` | Identifier of the user who owns the transaction |
| `amount` | Monetary value associated with the transaction |
| `categoryId` | Identifier of the category associated with the transaction |
| `date` | Date on which the transaction occurred |
| `description` | Optional description providing additional context |
| `paymentMethod` | Mode of payment used for the transaction |

### Purpose

The Transaction entity forms the primary source of financial data in Finance Lens. Transactions are used to calculate spending totals, category-wise spending, trends, budget utilization, and financial insights.

### Relationship

One User can have multiple Transactions.



## 3. Budget

The Budget represents the spending limit established by a user for a specific month.

### Attributes

| Attribute | Description |
|---|---|
| `id` | Unique identifier for the budget |
| `userId` | Identifier of the user who owns the budget |
| `amount` | Maximum planned spending amount for the period |
| `month` | Month to which the budget applies |
| `year` | Year to which the budget applies |

### Purpose

The Budget entity allows Finance Lens to compare planned spending with actual spending. It is used to calculate remaining budget, budget utilization, and budget-related financial insights.

### Relationship

One User can have multiple Budgets, with at most one budget associated with a specific month and year.



## 4. Category

The Category represents a classification used to organize financial transactions based on their purpose.

### Attributes

| Attribute | Description |
|---|---|
| `id` | Unique identifier for the category |
| `name` | Name of the category, such as Food, Transport, or Shopping |

### Purpose

The Category entity provides a consistent classification system for transactions and enables Finance Lens to perform category-wise spending analysis.

### Relationship

One Category can be associated with multiple Transactions.



## 5. Derived Data and Analytics

Analytics is not represented as a separate stored entity in the initial version of Finance Lens.

Analytical values such as total spending, remaining budget, budget utilization, category-wise spending, and spending trends will be calculated from the stored transaction, budget, and category data.

This approach avoids unnecessary duplication of derived information and ensures that analytical results remain consistent with the underlying financial records.