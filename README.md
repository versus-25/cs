https://ivan-shamaev.ru/data-engineering-etl-pipeline-data-warehouse-datalake/
https://tproger.ru/curriculum/data-engineer-interview-guide/
## SQL


#### DDL – Data Definition Language
CREATE – используется для создания объектов базы данных;
ALTER – используется для изменения объектов базы данных;
DROP – используется для удаления объектов базы данных.

#### DML – Data Manipulation Language
SELECT – осуществляет выборку данных;
INSERT – добавляет новые данные;
UPSERT
REPLACE
UPDATE – изменяет существующие данные;
DELETE – удаляет данные.

#### DCL – Data Control Language
GRANT – предоставляет пользователю или группе разрешения на определённые операции с объектом;
REVOKE – отзывает выданные разрешения;
DENY– задаёт запрет, имеющий приоритет над разрешением.

#### TCL – Transaction Control Language
BEGIN TRANSACTION – служит для определения начала транзакции;
COMMIT TRANSACTION – применяет транзакцию;
ROLLBACK TRANSACTION – откатывает все изменения, сделанные в контексте текущей транзакции;
SAVE TRANSACTION – устанавливает промежуточную точку сохранения внутри транзакции.

---

##### Транзакция  
- упорядоченное множество операций, переводящих базу данных из одного согласованного состояния в другое. Потом 
**COMMIT** - применяем изменения
**ROLLBACK** - откатываем изменения
До закрытия транзакции изменения сохраняются «виртуально»  и после коммита применяются фактически.
Если не делать коммит или ролбек и вернуть конекш(подключение) в пул подключений, то другой человек можем подтвердить изменения прошлого
###### Проблемы параллельного использования транзакций:
1. **Потерянное обновление** - когда у нас в результате изменения блока данных разными транзакциями, сохраняется только последняя.
2. **Грязное чтение** - когда мы можем прочитать данные, которые в последствии откатятся.
3. **Неповторяющееся** чтение - когда у нас в рамках одной транзакции. Чтение одних и тех же данных даёт разный результат 
4. **Фантомное чтение** - когда у нас в рамках одной транзакции есть выборка нескольких строк, а в итоге мы получаем разное количество. 

###### Уровни изоляции транзакций:
1. **Read uncommitted (чтение незафиксированных данных)** - Типичный способ реализации данного уровня изоляции — блокировка данных на время выполнения команды изменения, что гарантирует, что команды изменения одних и тех же строк, запущенные параллельно, фактически выполнятся последовательно, и ни одно из изменений не потеряется. Транзакции, выполняющие только чтение, при данном уровне изоляции никогда не блокируются.
2. **Read committed (чтение фиксированных данных)** - пишущая транзакция блокирует изменяемые данные для читающих транзакций, работающих на уровне read committed или более высоком, до своего завершения, препятствуя, таким образом, «грязному» чтению, а данные, блокируемые читающей транзакцией, освобождаются сразу после завершения операции SELECT
3. **Repeatable read (повторяющееся чтение)** - Блокировки в разделяющем режиме применяются ко всем данным, считываемым любой инструкцией транзакции, и сохраняются до её завершения. Это запрещает другим транзакциям изменять строки, которые были считаны незавершённой транзакцией. Однако другие транзакции могут вставлять новые строки, соответствующие условиям поиска инструкций, содержащихся в текущей транзакции.
4. **Serializable (упорядочиваемость)** - Самый высокий уровень изолированности; транзакции полностью изолируются друг от друга, каждая выполняется так, как будто параллельных транзакций не существует. Только на этом уровне параллельные транзакции не подвержены эффекту «фантомного чтения».

####### ACID
**Atomicity — Атомарность** гарантирует, что никакая транзакция не будет зафиксирована в системе частично. Будут либо выполнены все её подоперации, либо не выполнено ни одной.


Индекс в базах данных — это файл с последовательностью пар ключей и указателей
