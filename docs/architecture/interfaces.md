# Component Interfaces

Документ описує основні контракти взаємодії між компонентами
Task Manager.

Інтерфейси визначають операції, вхідні та вихідні дані,
помилки і пов'язані вимоги.

## ITaskService

Відповідальність:
координує виконання основних use cases для роботи із задачами.

| Операція     | Вхід               | Вихід     | Помилки / умови         | Вимога |
|--------------|--------------------|-----------|-------------------------|-------|
| createTask   | CreateTaskCommand  | TaskDto   | ValidationError         | FR-01 |
| changeStatus | TaskId, TaskStatus | TaskDto   | InvalidStatusTransition | FR-03 |
| searchTasks  | SearchCriteria     | TaskDto[] | –                       | FR-05 |

## ITaskRepository

Відповідальність:
забезпечує абстракцію доступу до persistence.

| Операція | Вхід | Вихід | Помилки / умови | Вимога |
|---|---|---|---|---|
| save | Task | Task | PersistenceError | FR-01 |
| findById | TaskId | Task? | PersistenceError | FR-03 |
| listByOwner | UserId | Task[] | PersistenceError | FR-02 |

## INotificationPort

Відповідальність:
передає повідомлення про події, пов'язані із задачами.

| Операція | Вхід | Вихід | Помилки / умови | Вимога |
|---|---|---|---|---|
| notifyTaskCreated | TaskCreatedEvent | void | не повинна блокувати основний use case | NFR-03 / FR-01 |
