---
title: "Функция COLUMNS_UPDATED (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLUMNS_UPDATED_TSQL
- COLUMNS_UPDATED
dev_langs:
- TSQL
helpviewer_keywords:
- COLUMNS_UPDATED function
- testing columns
- column testing [SQL Server]
- updated columns
ms.assetid: 765fde44-1f95-4015-80a4-45388f18a42c
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8ddb7462ee985ee62efa70455d27c91a51193124
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="columnsupdated-transact-sql"></a>COLUMNS_UPDATED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **varbinary** битовый шаблон, указывающий на столбцы в таблицу или представление, которое были вставлены или обновлены. Функция COLUMNS_UPDATED используется в теле триггера [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT или UPDATE для проверки возможности выполнения триггером определенных операций.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COLUMNS_UPDATED ( )   
```  
  
## <a name="return-types"></a>Возвращаемые типы
**varbinary**
  
## <a name="remarks"></a>Замечания  
Функция COLUMNS_UPDATED проверяет возможность выполнения операций триггером UPDATE или INSERT над множеством столбцов. Чтобы протестировать для инструкций UPDATE или INSERT попыток на один столбец, используйте [UPDATE()](../../t-sql/functions/update-trigger-functions-transact-sql.md).
  
Функция COLUMNS_UPDATED возвращает один или более байтов, которые упорядочены слева направо по принципу: крайний правый бит — наименее значащий бит в байте. Крайний правый бит крайнего левого байта представляет первый столбец в таблице, следующий бит слева представляет второй столбец и так далее. Функция COLUMNS_UPDATED возвращает множество байт, если таблица в которой триггер создается, содержит более чем восемь столбцов, с наименее значащим байтом в крайней левой позиции. Функция COLUMNS_UPDATED возвращает значение TRUE для всех столбцов при операциях INSERT, поскольку при вставке столбцам присваиваются явно указанные значения или неявные значения (NULL).
  
Чтобы проверить обновление и вставку в определенные столбцы, следуйте синтаксису битовых операторов и целой битовой маске проверяемого столбца. Например, в таблице **t1** содержит столбцы **C1**, **C2**, **C3**, **C4**, и **C5** . Чтобы проверить что столбцы **C2**, **C3**, и **C4** являются обновлены (с таблицей **t1** под действием триггера UPDATE), следуйте синтаксису **& 14**. Для проверки только столбец **C2** будет обновлен, укажите **& 2**.
  
Функция COLUMNS_UPDATED может быть использована внутри триггера языка [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT или UPDATE.
  
Столбец ORDINAL_POSITION представления INFORMATION_SCHEMA.COLUMNS несовместим с битовым шаблоном столбцов, возвращаемым функцией COLUMNS_UPDATED. Чтобы получить битовый шаблон, совместимый с функцией COLUMNS_UPDATED, обратитесь к свойству `ColumnID` системной функции `COLUMNPROPERTY` при запросе представления `INFORMATION_SCHEMA.COLUMNS`, как показано в следующем примере:
  
```sql
SELECT TABLE_NAME, COLUMN_NAME,  
    COLUMNPROPERTY(OBJECT_ID(TABLE_SCHEMA + '.' + TABLE_NAME),  
    COLUMN_NAME, 'ColumnID') AS COLUMN_ID  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = 'Person';  
```  
  
## <a name="column-sets"></a>Наборы столбцов
Если в таблице определен набор столбцов, функция COLUMNS_UPDATED действует следующими способами.
-   Если столбец из набора столбцов явным образом обновляется, соответствующему биту для этого столбца присваивается значение 1, а биту для набора столбцов присваивается значение 1.  
-   Если набор столбцов явным образом обновляется, биту для набора столбцов присваивается значение 1 и биты для всех разреженных столбцов в этой таблице получают значение 1.  
-   При операциях вставки всем битам присваивается значение 1.  
  
     Поскольку при изменениях в наборе столбцов битам для всех столбцов в наборе столбцов присваивается значение 1, столбцы в наборе столбцов, не подвергавшиеся изменениям, будут выглядеть как измененные. Дополнительные сведения о наборах столбцов см. в разделе [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-columnsupdated-to-test-the-first-eight-columns-of-a-table"></a>A. Использование функции COLUMNS_UPDATED для проверки первых восьми столбцов таблицы  
В следующем примере создаются две таблицы, `employeeData` и `auditEmployeeData`. Таблица `employeeData` содержит сведения о заработной плате служащих и может быть изменена членами отдела кадров. Если номер социальной страховки (SSN), ежегодная заработная плата или номер банковского счета служащего изменен, то создается запись аудита и вставляется в таблицу аудита `auditEmployeeData`.
  
С помощью функции `COLUMNS_UPDATED()` можно выполнить быструю проверку всех изменений в столбцах, которые содержат важные сведения о служащих. Использование функции `COLUMNS_UPDATED()` таким способом будет оправдано, только если пытаться выявить изменения в первых восьми столбцах таблицы.
  
```sql
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_NAME = 'employeeData')  
   DROP TABLE employeeData;  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_NAME = 'auditEmployeeData')  
   DROP TABLE auditEmployeeData;  
GO  
CREATE TABLE dbo.employeeData (  
   emp_id int NOT NULL PRIMARY KEY,  
   emp_bankAccountNumber char (10) NOT NULL,  
   emp_salary int NOT NULL,  
   emp_SSN char (11) NOT NULL,  
   emp_lname nchar (32) NOT NULL,  
   emp_fname nchar (32) NOT NULL,  
   emp_manager int NOT NULL  
   );  
GO  
CREATE TABLE dbo.auditEmployeeData (  
   audit_log_id uniqueidentifier DEFAULT NEWID() PRIMARY KEY,  
   audit_log_type char (3) NOT NULL,  
   audit_emp_id int NOT NULL,  
   audit_emp_bankAccountNumber char (10) NULL,  
   audit_emp_salary int NULL,  
   audit_emp_SSN char (11) NULL,  
   audit_user sysname DEFAULT SUSER_SNAME(),  
   audit_changed datetime DEFAULT GETDATE()  
   );  
GO  
CREATE TRIGGER dbo.updEmployeeData   
ON dbo.employeeData   
AFTER UPDATE AS  
/*Check whether columns 2, 3 or 4 have been updated. If any or all  
columns 2, 3 or 4 have been changed, create an audit record. The
bitmask is: power(2,(2-1))+power(2,(3-1))+power(2,(4-1)) = 14. To test   
whether all columns 2, 3, and 4 are updated, use = 14 instead of >0  
(below).*/
  
   IF (COLUMNS_UPDATED() & 14) > 0  
/*Use IF (COLUMNS_UPDATED() & 14) = 14 to see whether all columns 2, 3,   
and 4 are updated.*/  
      BEGIN  
-- Audit OLD record.  
      INSERT INTO dbo.auditEmployeeData  
         (audit_log_type,  
         audit_emp_id,  
         audit_emp_bankAccountNumber,  
         audit_emp_salary,  
         audit_emp_SSN)  
         SELECT 'OLD',   
            del.emp_id,  
            del.emp_bankAccountNumber,  
            del.emp_salary,  
            del.emp_SSN  
         FROM deleted del;  
  
-- Audit NEW record.  
      INSERT INTO dbo.auditEmployeeData  
         (audit_log_type,  
         audit_emp_id,  
         audit_emp_bankAccountNumber,  
         audit_emp_salary,  
         audit_emp_SSN)  
         SELECT 'NEW',  
            ins.emp_id,  
            ins.emp_bankAccountNumber,  
            ins.emp_salary,  
            ins.emp_SSN  
         FROM inserted ins;  
   END;  
GO  
  
/*Inserting a new employee does not cause the UPDATE trigger to fire.*/  
INSERT INTO employeeData  
   VALUES ( 101, 'USA-987-01', 23000, 'R-M53550M', N'Mendel', N'Roland', 32);  
GO  
  
/*Updating the employee record for employee number 101 to change the   
salary to 51000 causes the UPDATE trigger to fire and an audit trail to   
be produced.*/  
  
UPDATE dbo.employeeData  
   SET emp_salary = 51000  
   WHERE emp_id = 101;  
GO  
SELECT * FROM auditEmployeeData;  
GO  
  
/*Updating the employee record for employee number 101 to change both   
the bank account number and social security number (SSN) causes the   
UPDATE trigger to fire and an audit trail to be produced.*/  
  
UPDATE dbo.employeeData  
   SET emp_bankAccountNumber = '133146A0', emp_SSN = 'R-M53550M'  
   WHERE emp_id = 101;  
GO  
SELECT * FROM dbo.auditEmployeeData;  
  
GO  
```  
  
### <a name="b-using-columnsupdated-to-test-more-than-eight-columns"></a>Б. Использование функции COLUMNS_UPDATED для проверки более чем восьми столбцов  
Чтобы проверить обновления других столбцов таблицы, кроме первых восьми, используйте функцию `SUBSTRING` для проверки корректности бита, возвращенного функцией `COLUMNS_UPDATED`. В следующем примере проверяется наличие обновлений, которые влияют на столбцы `3`, `5`, и `9` в `AdventureWorks2012.Person.Person` таблицы.
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Person.uContact2', N'TR') IS NOT NULL  
    DROP TRIGGER Person.uContact2;  
GO  
CREATE TRIGGER Person.uContact2 ON Person.Person  
AFTER UPDATE AS  
    IF ( (SUBSTRING(COLUMNS_UPDATED(),1,1) & 20 = 20)   
        AND (SUBSTRING(COLUMNS_UPDATED(),2,1) & 1 = 1) )   
    PRINT 'Columns 3, 5 and 9 updated';  
GO  
  
UPDATE Person.Person   
   SET NameStyle = NameStyle,  
      FirstName=FirstName,  
      EmailPromotion=EmailPromotion;  
GO  
```  
  
## <a name="see-also"></a>См. также:
[Побитовые операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
[CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
[Обновление &#40; &#41; &#40; Transact-SQL &#41;](../../t-sql/functions/update-trigger-functions-transact-sql.md)
  
  
