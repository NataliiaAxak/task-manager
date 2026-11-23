# ADR-002: Відокремити persistence через Repository / Port

Status: Accepted

Date: 2026-11-03

## Context

Бізнес-логіка не повинна залежати безпосередньо
від SQLite або конкретної бібліотеки доступу до даних.

Це пов'язано з NFR-01 Maintainability та вимогами до testability.

## Decision Drivers

- можливість тестувати Application/Domain без реальної БД;
- зменшення coupling;
- можливість заміни persistence implementation;
- чіткі межі між логікою та Infrastructure.

## Considered Options

1. TaskService безпосередньо використовує SQLite.
2. TaskService залежить від ITaskRepository.
3. Використати глобальний static data access class.

## Decision

Визначити контракт:

ITaskRepository

Application залежить від цього контракту.

Infrastructure містить реалізацію:

SqliteTaskRepository

## Rationale

Залежність від abstraction дозволяє ізолювати
business logic від persistence technology.

Це також дозволяє підмінити repository
mock або in-memory implementation під час тестування.

## Consequences

### Positive

- нижчий coupling;
- вища testability;
- простіша заміна способу зберігання;
- чіткіша архітектурна boundary.

### Negative / Risks

- з'являється додатковий abstraction layer;
- збільшується кількість interfaces і classes.

## Related

- NFR-01;
- ASR-01;
- Issue #7;
- docs/uml/components.puml;
- docs/architecture/architecture.md.
