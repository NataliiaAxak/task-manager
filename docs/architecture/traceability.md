# Traceability Matrix

| Requirement | Use Case / UML | Component | ADR | Interface | Як перевіряється |
|---|---|---|---|---|---|
| FR-01 | UC Create Task; Create Task Sequence | Presentation, Application, Infrastructure | ADR-001, ADR-002 | ITaskService, ITaskRepository | acceptance criteria / test |
| FR-02 | UC View Tasks | Application, Infrastructure | ADR-002 | ITaskRepository | test listByOwner |
| FR-03 | UC Change Status | Domain, Application | ADR-001 | ITaskService | domain rule test |
| FR-05 | UC Search Tasks | Application, Infrastructure | ADR-001 | ITaskService | search test |
| NFR-01 | Component Diagram | Application, Domain, Infrastructure | ADR-001, ADR-002 | ITaskRepository | unit tests without SQLite |
| NFR-02 | Architecture / Configuration | Infrastructure | ADR-001 | – | repository audit |
