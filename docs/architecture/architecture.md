# Architecture

## 1. Context and Scope

Task Manager – навчальна система керування особистими задачами.
Основний користувач – User.

## 2. Architecture Drivers

| Driver             | Вплив на архітектуру                                         |
|--------------------|--------------------------------------------------------------|
| Maintainability    | розділити UI, application logic і persistence                |
| Testability        | бізнес-логіка не повинна залежати від SQLite                 |
| Security           | secrets і локальна конфігурація не зберігаються у repository |
| Performance        | уникати зайвих викликів і неефективного доступу до даних     |
| Small project size | не потрібна складна distributed architecture                 |
| SQLite constraint  | persistence реалізується локально                            |

## 3. Architecture Alternatives

### A1 – Modular Monolith + Layers
...

### A2 – Microservices
...

## 4. Chosen Architecture

Обрано Modular Monolith + Layered Architecture.

## 5. Components and Responsibilities

| Component      | Responsibility                     |
|----------------|------------------------------------|
| Presentation   | UI/API interaction                 |
| Application    | use case orchestration             |
| Domain         | business rules                     |
| Infrastructure | persistence and technical adapters |
| SQLite         | data storage                       |

## 6. Dependencies

Presentation → Application → Domain

Infrastructure реалізує persistence contracts.

## 7. Data Storage

Основне локальне сховище – SQLite.

## 8. Quality Attributes

- maintainability;
- testability;
- security;
- performance.

## 9. Constraints

- C#;
- .NET 10;
- SQLite;
- Git;
- documentation in docs/.

## 10. Risks and Open Questions

- можливе зростання складності Domain;
- необхідність контролю coupling;
- performance SQLite потрібно перевірити під час реалізації;
- authentication ще не деталізована.

## 11 Requirement to Architecture Mapping

| Requirement            | Architectural Decision                  |
|------------------------|-----------------------------------------|
| NFR-01 Maintainability | Layered separation                      |
| NFR-02 Security        | externalized secrets                    |
| NFR-03 Performance     | direct local persistence via SQLite     |
| FR-01 Create Task      | Presentation → Application → Repository |


