# Building Event Driven Microservices

- [1. Why event driven microservices](#why-event-driven-microservices)
  - [What are event driven microservices](#what-are-event-driven-microservices)
  - [Introduction to domain driven design and bounded contexts](#Introduction-to-domain-driven-design-and-bounded-contexts)
    - [Leveraging Domain models and bounded contexts](#leveraging-domain-models-and-bounded-contexts)
    - [Aligning Bounded Contexts with Business Requirements](#aligning-bounded-contexts-with-business-requirements)

## Why event driven microservices
- Network communnications, relational databases, big data developements and cloud computing have significantly altered how architectures are built.
- Have imapacted the way organizations, teams and people communicated with one another.
- Asynchromous events can now be persisted indefinitely at very large sccales and be consumed by any service as many times as necessary.
- compute resourcs can be easily acquired and released on demand, enabling the creation and mgmt of microservices (ms).

### What are event driven microservices
- Message passing architectures use consumable events to asynchronously communicate with one another. Event based communication helps handling big data sets, at scale and in real time,and thus asks change in the old architectural styles.
- In event driven ms (EDM) system communicated by issuing and consuming events. **These events are not destroyed upon consumption as in message passing systems, but remain readily available for other consumers to read as they require.**
- Services are small, created to help fufill necessaty business goals. They consume events from input event streams; apply their specific business logic; and may emit their own  output events, provide data for request-response access, communicate with a third-party API, or perform other required actions. 
- Services can be stateful or stateless, complex or simple; and they might be implemented as long-running, standalone applications or executed as a function using Functions-as-a-Service

### Introduction to domain driven design and bounded contexts
Some important terminology and defeinitions - 
  - Domain

    The problem space. Encompasses everything that the business must contend with, including rules, processes, ideas, business-specific terminology, and anything related to its problem space- regardless of whether or not the business concerns itself with. The domain exists regardless of the existence of the business.

 - Subdomain

    A component of the main domain. Each subdomain focuses on a specific subset of responsibilities and typically reflects some of the business’s organizational structure (such as Warehouse, Sales, and Engineering). A subdomain can be seen as a domain in its own right. Subdomains, like the domain itself, belong to the problem space.

 - Domain (and subdomain) model

    An abstraction of the actual domain useful for business purposes. The pieces and properties of the domain that are most important to the business are used to generate the model. The main domain model of an business is discernible through the products the business provides its customers, the interfaces by which customers interact with the products, and the various other processes and functions by which the business fulfills its stated goals. Models often need to be refined as the domain changes and as business priorities shift. A domain model is part of the solution space, as it is a construct the business uses to solve problems.

 - Bounded context

    The logical boundaries, including the inputs, outputs, events, requirements, processes, and data models, relevant to the subdomain. While ideally a bounded context and a subdomain will be in complete alignment, legacy systems, technical debt, and third-party integrations often create exceptions. Bounded contexts are also a property of the solution space and have a significant impact on how microservices interact with one another.

1.  Bounded contexts should be highly cohesive. 
2. Connections between bounded contexts should be loosely coupled, as changes made within one bounded context should minimize or eliminate the impact on neighboring contexts

#### Leveraging Domain models and bounded contexts
- The domain is broken down into subdomains—perhaps, for a technology-centric company, an Engineering department, a Sales department, and a Customer Support department. 
- Each subdomain has its own requirements and duties and may itself be subdivided. This division process repeats until the subdomain models are granular and actionable and can be translated into small and independent services by the implementing teams.
- Bounded contexts are established around these subdomains and form the basis for the creation of microservices.

### Aligning Bounded Contexts with Business Requirements
- bounded contexts should be built around business requirements and not technological requirements as it is common for the business requirements of a product to change during its lifetime.
- Aligning bounded contexts on business requirements allows teams to make changes to microservice implementations in a loosely coupled and highly cohesive way