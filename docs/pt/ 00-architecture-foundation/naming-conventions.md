# AI-Commerce Platform
# Naming Conventions Standard

---

## Document Information

| Attribute | Value |
|---|---|
| Document Type | Engineering Standard |
| Document ID | STD-005 |
| Version | 1.0 |
| Status | Active |
| Owner | Architecture Team |
| Domain | Software Engineering |
| Last Updated | 2026 |

---

# 1. Purpose

This document defines naming conventions and standards used across the AI-Commerce Platform.

The objective is to establish consistency across:

- source code;
- microservices;
- APIs;
- databases;
- events;
- cloud resources;
- infrastructure components;
- documentation.

Consistent naming improves:

- readability;
- maintainability;
- collaboration;
- automation;
- operational management.

---

# 2. Naming Principles

The platform follows these principles:

## 2.1 Clarity Over Short Names

Names must represent business meaning.

Preferred:

```
CustomerAuthenticationService
```

Avoid:

```
AuthSvc
CAS
Service01
```

---

## 2.2 Business Language First

Names should reflect domain concepts.

Example:

Preferred:

```
OrderCreatedEvent
```

Avoid:

```
TransactionMessage
```

The first represents a business event.

The second represents a technical implementation.

---

## 2.3 Consistency Across Layers

The same concept must maintain consistent naming.

Example:

Business Concept:

```
Customer
```

Should appear consistently as:

```
Customer
CustomerService
CustomerRepository
CustomerCreatedEvent
customer_id
```

---

# 3. Repository Naming

Repositories must follow:

```
<domain>-<type>
```

Examples:

```
ai-commerce-auth-service

ai-commerce-product-service

ai-commerce-order-service

ai-commerce-architecture

ai-commerce-infrastructure
```

Rules:

- lowercase;
- words separated by hyphen;
- no abbreviations.

---

# 4. Microservice Naming

Microservices represent business capabilities.

Pattern:

```
<business-capability>-service
```

Examples:

```
auth-service

product-service

order-service

inventory-service
```

AI-specific services:

```
ai-support-agent

recommendation-agent

pricing-agent
```

Avoid:

```
ai-service-v2
service-manager
backend-api
```

---

# 5. Java Package Naming

Java packages follow:

```
com.aicommerce.<service>
```

Example:

```
com.aicommerce.auth_service
```

Recommended structure:

```
com.aicommerce.order_service

├── domain
├── application
├── infrastructure
└── adapters
```

---

# 6. Java Class Naming

## Classes

Use PascalCase.

Examples:

```
OrderService

CustomerController

PaymentProcessor
```

---

## Interfaces

Use meaningful names.

Examples:

```
PaymentGateway

NotificationSender

OrderRepository
```

Avoid:

```
IPaymentService
IOrderRepository
```

The prefix "I" is not recommended in modern Java practices.

---

## Implementations

Use descriptive suffixes.

Examples:

```
OrderRepositoryAdapter

KafkaEventPublisher

PostgresCustomerRepository
```

---

# 7. Method Naming

Methods must use camelCase.

Examples:

```
createOrder()

findCustomerById()

calculateTotalAmount()
```

Use verbs:

```
create
update
delete
calculate
validate
process
publish
consume
```

Avoid generic names:

```
doSomething()

execute()

handle()
```

---

# 8. Variable Naming

Variables must use camelCase.

Examples:

```
customerId

orderItems

totalAmount

createdAt
```

Avoid:

```
x

temp

obj

data
```

---

# 9. Database Naming

## Tables

Use snake_case and plural names.

Examples:

```
customers

orders

order_items

products
```

---

## Columns

Use snake_case.

Examples:

```
customer_id

created_at

updated_at

total_amount
```

---

## Primary Keys

Preferred:

```
id
```

Example:

```
orders

id
customer_id
status
created_at
```

---

## Foreign Keys

Pattern:

```
<table>_id
```

Examples:

```
customer_id

product_id

order_id
```

---

# 10. API Naming Standards

REST endpoints use:

```
/api/v{version}/{resource}
```

Example:

```
/api/v1/products

/api/v1/orders

/api/v1/customers
```

---

## Resource Naming

Use plural nouns.

Correct:

```
GET /products
```

Incorrect:

```
GET /getProducts
```

---

## Actions

Actions should be represented by HTTP methods.

Example:

Create:

```
POST /orders
```

Update:

```
PUT /orders/{id}
```

Delete:

```
DELETE /orders/{id}
```

---

# 11. Event Naming

Events represent facts that already happened.

Pattern:

```
<Entity><PastTenseAction>Event
```

Examples:

```
OrderCreatedEvent

ProductUpdatedEvent

CustomerRegisteredEvent
```

Rules:

- use past tense;
- represent completed actions;
- immutable.

Avoid:

```
CreateOrderEvent

UpdateProductMessage
```

---

# 12. Kafka Topic Naming

Pattern:

```
<domain>.<entity>.<event>
```

Examples:

```
commerce.order.created

commerce.product.updated

commerce.customer.registered
```

Rules:

- lowercase;
- dot notation;
- domain oriented.

---

# 13. API DTO Naming

Request:

```
<Create><Entity>Request
```

Examples:

```
CreateOrderRequest

RegisterUserRequest
```

Response:

```
<Entity>Response
```

Examples:

```
OrderResponse

UserResponse
```

---

# 14. Configuration Naming

Use lowercase kebab-case.

Examples:

```
application.yml

application-prod.yml

application-test.yml
```

Environment variables:

Use uppercase snake_case.

Examples:

```
DATABASE_URL

KAFKA_BOOTSTRAP_SERVERS

JWT_SECRET
```

---

# 15. Cloud Resource Naming

Pattern:

```
<project>-<environment>-<resource>
```

Examples:

```
aicommerce-prod-api

aicommerce-dev-database

aicommerce-prod-cluster
```

Environments:

```
dev

test

staging

prod
```

---

# 16. Branch Naming

Git branches follow:

```
<type>/<description>
```

Examples:

Feature:

```
feature/project-vision
```

Bug fix:

```
bugfix/auth-token-expiration
```

Documentation:

```
docs/architecture-quality-model
```

Hotfix:

```
hotfix/payment-error
```

---

# 17. Commit Naming

The platform follows Conventional Commits.

Format:

```
type(scope): description
```

Examples:

Documentation:

```
docs(project-vision): create architecture vision document
```

Feature:

```
feat(order-service): implement order creation flow
```

Fix:

```
fix(auth-service): correct token validation
```

---

# 18. AI Component Naming

AI components must represent their responsibility.

Examples:

```
CustomerSupportAgent

RecommendationAgent

PricingOptimizationAgent
```

AI artifacts:

```
customer-support-prompt

product-recommendation-model

customer-memory-store
```

---

# 19. Architecture Documentation Naming

Documents follow:

```
<number>-<topic>
```

Examples:

```
00-architecture-foundation

01-project-vision

02-business-domain

03-quality-attributes

04-system-context
```

---

# 20. Naming Anti-Patterns

Avoid:

```
CommonService

Utils

Manager

Helper

GenericProcessor

DataObject
```

unless the responsibility is extremely clear.

Prefer domain terminology.

---

# 21. Governance

All new components must follow these conventions.

Exceptions require architectural review.

Naming decisions must prioritize:

1. business clarity;
2. consistency;
3. maintainability;
4. operational simplicity.

---

# References

- Domain-Driven Design
- Clean Architecture
- REST API Design Guidelines
- Twelve-Factor Application
- Cloud Native Computing Foundation Practices
- Enterprise Software Engineering Standards
