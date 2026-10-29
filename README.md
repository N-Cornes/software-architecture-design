# Software Architecture & Design

A software architecture project focused on evaluating architectural styles, selecting designs based on system requirements, and refactoring a monolithic retail application into independently deployed services.

## Project Focus

The project compares multiple software architecture patterns across different system scenarios:

- **Retail environment:** Microservices architecture
- **Event ticketing system:** Client-server architecture
- **Order processing system:** Event-driven architecture

Each architecture was evaluated based on scalability, maintainability, deployment flexibility, communication patterns, and cloud suitability.

## Retail System Refactor

The original retail application used a monolithic structure where one `RetailSystem` directly created and controlled cart, payment, and inventory functionality.

The system was refactored into separate Python services:

- `cart_service.py` — cart operations
- `inventory_service.py` — inventory operations
- `payment_service.py` — payment processing
- `orchestrator_service.py` — coordinates the checkout workflow across services

## Service Architecture

```text
Client
  ↓
Orchestrator Service :5000
  ↓
  ├── Inventory Service :5001
  ├── Cart Service      :5002
  └── Payment Service   :5003
```

The orchestrator manages the checkout sequence and coordinates communication between the individual services instead of allowing one monolithic application to control every responsibility directly.

## Checkout Flow

```text
Checkout Request
      ↓
Orchestrator
      ↓
Inventory Validation
      ↓
Cart Processing
      ↓
Payment Processing
      ↓
Checkout Result
```

## Architecture Concepts Demonstrated

- Monolith-to-microservices refactoring
- Separation of responsibilities
- Service orchestration
- Independent service boundaries
- Distributed system communication
- Scalability and maintainability tradeoffs
- Client-server architecture
- Event-driven architecture
- Cloud-oriented deployment planning

## Why Microservices for the Retail Scenario?

Separating cart, inventory, and payment responsibilities allows each capability to be maintained and deployed independently. This reduces coupling compared with the original monolithic design and makes it easier to scale or modify one part of the system without redeploying the entire application.

## Cloud Deployment

The architecture analysis recommends cloud deployment for the evaluated systems so infrastructure can scale with demand while supporting centralized monitoring, availability, and independent application components.

## Source Code

The original implementation and academic deliverables are maintained in a private repository. Source access can be provided for professional review upon request.

## Author

**Nicholas Cornes**  
B.S. Software Engineering
