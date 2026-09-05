# Abbreviations and Technical Language

Use this note when a question is written in compressed technical language. Expand the short form first, then identify the layer: language, framework, database, protocol, architecture, process, or security.

## JD and business terms

| Short form | Full form | Meaning in this test |
|---|---|---|
| CRM | Customer Relationship Management | Software that manages customer, lead, sales, and interaction data |
| JD | Job Description | Role requirements supplied by the company |
| BE/BTech | Bachelor of Engineering/Bachelor of Technology | Degree requirement |
| CS | Computer Science | Academic/technical field |
| IT | Information Technology | Academic/technical field |
| OOP/OOPs | Object-Oriented Programming | Organizing software around objects |
| SDLC | Software Development Life Cycle | Requirements through maintenance |
| QA | Quality Assurance | Activities that prevent and detect defects |
| UI | User Interface | What the user sees and operates |
| UX | User Experience | Overall usability and interaction quality |
| Figma | — | Collaborative UI design/prototyping tool |

## Languages, stacks, and frameworks

| Short form | Full form                         | Meaning                                                       |
| ---------- | --------------------------------- | ------------------------------------------------------------- |
| JVM        | Java Virtual Machine              | Executes Java bytecode                                        |
| JRE        | Java Runtime Environment          | JVM plus runtime libraries                                    |
| JDK        | Java Development Kit              | JRE plus development tools                                    |
| PHP        | PHP: Hypertext Preprocessor       | Server-side scripting language                                |
| JS         | JavaScript                        | Programming language for web and other runtimes               |
| HTML       | HyperText Markup Language         | Web document structure                                        |
| CSS        | Cascading Style Sheets            | Web presentation and layout                                   |
| DOM        | Document Object Model             | In-memory representation of a webpage                         |
| AJAX       | Asynchronous JavaScript and XML   | Asynchronous browser-server communication; JSON is now common |
| Node.js    | —                                 | JavaScript runtime outside the browser                        |
| Express    | Express.js                        | Node.js web framework                                         |
| React      | React.js                          | JavaScript UI library                                         |
| MERN       | MongoDB, Express, React, Node.js  | JavaScript-oriented full-stack combination                    |
| MVC        | Model-View-Controller             | Separation pattern for data, UI, and request coordination     |
| ORM        | Object-Relational Mapping         | Maps application objects to database records                  |
| API        | Application Programming Interface | Contract for software communication                           |
| REST       | Representational State Transfer   | Resource-oriented API style                                   |
| JSON       | JavaScript Object Notation        | Common data-exchange format                                   |
| BSON       | Binary JSON                       | MongoDB’s binary document representation                      |

## Databases and data

| Short form | Full form | Meaning |
|---|---|---|
| DB/DBMS | Database/Database Management System | Data storage / software managing it |
| SQL | Structured Query Language | Relational database language |
| NoSQL | Not Only SQL | Broad non-relational database category |
| CRUD | Create, Read, Update, Delete | Basic data operations |
| PK | Primary Key | Unique row identifier |
| FK | Foreign Key | Reference linking records |
| ACID | Atomicity, Consistency, Isolation, Durability | Transaction guarantees |
| ERD | Entity-Relationship Diagram | Diagram of entities and relationships |
| N+1 | N plus one query problem | One query for a list plus one per item |
| TTL | Time To Live | Automatic expiry duration for data/cache |
| BSON | Binary JSON | MongoDB storage/query representation |

## HTTP and API language

| Short form | Full form                              | Meaning                                             |
| ---------- | -------------------------------------- | --------------------------------------------------- |
| HTTP       | HyperText Transfer Protocol            | Web request/response protocol                       |
| HTTPS      | HTTP Secure                            | HTTP protected by TLS                               |
| URL        | Uniform Resource Locator               | Address of a resource                               |
| URI        | Uniform Resource Identifier            | Identifier for a resource; URL is a common URI type |
| TCP        | Transmission Control Protocol          | Reliable transport protocol                         |
| TLS        | Transport Layer Security               | Encryption/authentication layer for network traffic |
| CORS       | Cross-Origin Resource Sharing          | Browser-controlled cross-origin access policy       |
| JWT        | JSON Web Token                         | Signed token format for claims                      |
| MIME       | Multipurpose Internet Mail Extensions  | Content type notation such as `application/json`    |
| DNS        | Domain Name System                     | Maps domain names to network addresses              |
| REST API   | REST Application Programming Interface | API following REST-style conventions                |
| SLA        | Service Level Agreement                | Agreed service target                               |
| SLI/SLO    | Service Level Indicator/Objectives     | Measurement and target for reliability              |

## Testing, development, and delivery

| Short form | Full form                          | Meaning                                        |
| ---------- | ---------------------------------- | ---------------------------------------------- |
| CI         | Continuous Integration             | Frequently integrating and testing changes     |
| CD         | Continuous Delivery/Deployment     | Automatically preparing or releasing changes   |
| TDD        | Test-Driven Development            | Write a failing test, implement, then refactor |
| BDD        | Behavior-Driven Development        | Specify behavior in user/business language     |
| E2E        | End-to-End                         | Test of a complete user/system flow            |
| UAT        | User Acceptance Testing            | Business/user validation                       |
| RCA        | Root Cause Analysis                | Finding why a problem occurred                 |
| PR/MR      | Pull Request/Merge Request         | Review and integration proposal                |
| VCS        | Version Control System             | Tracks file history and collaboration          |
| Git        | —                                  | Distributed VCS                                |
| IDE        | Integrated Development Environment | Code editor plus development tools             |
| SDK        | Software Development Kit           | Tools/libraries for a platform                 |
| CLI        | Command-Line Interface             | Terminal-based interaction                     |
| API        | Application Programming Interface  | Also used in tooling/development context       |

## Cloud and operations

| Short form | Full form | Meaning |
|---|---|---|
| AWS | Amazon Web Services | Cloud provider |
| GCP | Google Cloud Platform | Cloud provider |
| VM | Virtual Machine | Software-defined computer |
| IaaS | Infrastructure as a Service | Virtual infrastructure provided by cloud |
| PaaS | Platform as a Service | Managed application platform |
| SaaS | Software as a Service | Complete software delivered as a service |
| IAM | Identity and Access Management | Cloud identities and permissions |
| CDN | Content Delivery Network | Distributed content delivery |
| DNS | Domain Name System | Domain-to-address resolution |
| LB | Load Balancer | Distributes traffic |
| S3 | Simple Storage Service | AWS object storage service name |
| GCS | Google Cloud Storage | Google object storage service |
| VM | Virtual Machine | Compute abstraction |
| VPC | Virtual Private Cloud | Isolated virtual network |
| RTO/RPO | Recovery Time/Point Objective | Recovery time/data-loss targets |
| MTTR | Mean Time To Recovery/Repair | Average restoration time |
| SLA | Service Level Agreement | Service commitment |

## Security terms

| Short form | Full form | Meaning |
|---|---|---|
| CIA | Confidentiality, Integrity, Availability | Core security objectives |
| MFA/2FA | Multi-Factor/Two-Factor Authentication | More than one authentication factor |
| RBAC | Role-Based Access Control | Permissions assigned through roles |
| XSS | Cross-Site Scripting | Injected script executed in a browser |
| CSRF | Cross-Site Request Forgery | Forced action using a victim’s credentials |
| SQLi | SQL Injection | Input changes a database query |
| IDOR | Insecure Direct Object Reference | Unauthorized access by manipulating an object ID |
| DoS/DDoS | Denial-of-Service/Distributed DoS | Availability attack through resource exhaustion |
| TLS | Transport Layer Security | Network encryption/authentication |
| PII | Personally Identifiable Information | Data that can identify a person |
| OWASP | Open Worldwide Application Security Project | Security guidance/community |
| CVE | Common Vulnerabilities and Exposures | Public vulnerability identifier system |
| CORS | Cross-Origin Resource Sharing | Browser cross-origin policy |

## How to decode a complex question

If a question says “implement an idempotent RESTful endpoint with RBAC and ACID persistence,” decode it as: design a REST resource; make repeated requests safe; authenticate the caller; authorize by role; and update related database records in a transaction. If it says “optimize an N+1 query under horizontal scaling,” decode it as: reduce repeated database calls and ensure multiple application instances can serve requests without relying on local process memory.

## Final short-form drill

Before the test, explain these without looking: CRM, OOP, JVM, JDK, ORM, MVC, REST, CRUD, PK, FK, ACID, JSON, BSON, AJAX, DOM, JWT, CORS, CI/CD, API, RBAC, XSS, CSRF, SQLi, AWS, GCP, IAM, CDN, SLA, RTO, and RPO.
