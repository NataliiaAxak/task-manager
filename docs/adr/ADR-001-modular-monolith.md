# ADR-001: Використати Modular Monolith для MVP

Status: Accepted

Date: 2026-11-D3

## Context

Task Manager є невеликим навчальним програмним проєктом.

Система повинна бути:
- зрозумілою для розробки;
- підтримуваною;
- тестованою;
- простою для локального deployment.

Окреме масштабування підсистем не є вимогою.

Рішення повинно враховувати:
- NFR-01 Maintainability;
- вимоги до testability;
- невеликий розмір системи;
- використання .NET 10 та SQLite.

## Decision Drivers

- низька складність deployment;
- чіткий розподіл відповідальності;
- можливість тестувати business logic окремо;
- невеликий розмір проєкту;
- відсутність потреби у незалежному масштабуванні сервісів;
- мінімальні операційні витрати.

## Considered Options

1. Modular Monolith + Layered Architecture.
2. Microservices.
3. Простий моноліт без явного розділення на шари.

## Decision

Використовувати Modular Monolith із Layered Architecture.

Основні шари:

- Presentation;
- Application;
- Domain;
- Infrastructure.

## Rationale

Modular Monolith забезпечує простий deployment і не потребує
окремої інфраструктури для міжсервісної взаємодії.

Layered Architecture дозволяє розділити:
- взаємодію з користувачем;
- orchestration use cases;
- domain rules;
- persistence.

## Consequences

### Positive

- одна кодова база;
- простий deployment;
- чітке розділення відповідальності;
- зручніше тестування business logic;
- менша операційна складність.

### Negative / Risks

- компоненти не можуть масштабуватися незалежно;
- необхідно контролювати залежності між шарами;
- із ростом системи monolith може стати складнішим для супроводження.

## Related

- NFR-01 Maintainability;
- ASR-01;
- Issue #7;
- docs/architecture/architecture.md;
- docs/uml/components.puml.
________________________________________
