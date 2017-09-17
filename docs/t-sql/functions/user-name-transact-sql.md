---
title: "Имя_пользователя (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER_NAME
- USER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- IDs [SQL Server], databases
- USER_NAME function
- users [SQL Server], database username
- names [SQL Server], database users
- identification numbers [SQL Server], databases
- database usernames [SQL Server]
ms.assetid: ab32d644-4228-449a-9ef0-5a975c305775
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5179a5d031dbc654f1624f4d64c3e94bf28efe40
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="username-transact-sql"></a>USER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает имя пользователя базы данных по указанному идентификационному номеру.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
USER_NAME ( [ id ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *идентификатор*  
 Номер идентификатора, сопоставленный с пользователем базы данных. *Идентификатор*— **int**. Необходимо поставить скобки.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(256)**  
  
## <a name="remarks"></a>Замечания  
 Когда *идентификатор* — этот параметр опущен, подразумевается текущий пользователь в текущем контексте. Если параметр содержит слово NULL, то возвращается значение NULL. При вызове USER_NAME без указания *идентификатор* после EXECUTE как инструкции, функция USER_NAME возвращает имя олицетворенного пользователя. Если пользователь Windows попытается получить доступ к базе данных в качестве члена группы, функция USER_NAME вернет имя этого пользователя, а не имя группы.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-username"></a>A. Использование USER_NAME.  
 Следующий пример возвращает имя пользователя по его идентификатору `13`.  
  
```  
SELECT USER_NAME(13);  
GO  
```  
  
### <a name="b-using-username-without-an-id"></a>Б. Использование USER_NAME без идентификатора  
 Следующий пример демонстрирует поиск имени текущего пользователя без указания его идентификатора.  
  
```  
SELECT USER_NAME();  
GO  
```  
  
 Далее приведен результирующий набор для пользователя, который является членом предопределенной роли сервера sysadmin.  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="c-using-username-in-the-where-clause"></a>В. Использование USER_NAME в предложении WHERE  
 Следующий пример иллюстрирует поиск в таблице `sysusers` строки, имя которой равняется результату работы системной функции `USER_NAME` для пользователя с идентификационным номером, равным `1`.  
  
```  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `name`  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="d-calling-username-during-impersonation-with-execute-as"></a>Г. Вызов USER_NAME во время олицетворения пользователя с помощью EXECUTE AS  
 Следующий пример показывает, как `USER_NAME` ведет себя во время олицетворения пользователя.  
  
```  
SELECT USER_NAME();  
GO  
EXECUTE AS USER = 'Zelig';  
GO  
SELECT USER_NAME();  
GO  
REVERT;  
GO  
SELECT USER_NAME();  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DBO`  
  
 `Zelig`  
  
 `DBO`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-username"></a>Д. Использование USER_NAME.  
 Следующий пример возвращает имя пользователя по его идентификатору `13`.  
  
```  
SELECT USER_NAME(13);  
```  
  
### <a name="f-using-username-without-an-id"></a>Е. Использование USER_NAME без идентификатора  
 Следующий пример демонстрирует поиск имени текущего пользователя без указания его идентификатора.  
  
```  
SELECT USER_NAME();  
```  
  
 Ниже приведен результирующий набор для пользователя, вошедшего в систему.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------------------------   
User7                              
```  
  
### <a name="g-using-username-in-the-where-clause"></a>Ж. Использование USER_NAME в предложении WHERE  
 Следующий пример иллюстрирует поиск в таблице `sysusers` строки, имя которой равняется результату работы системной функции `USER_NAME` для пользователя с идентификационным номером, равным `1`.  
  
```  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
name                             
------------------------------   
User7                              
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40; Transact-SQL &#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [Функция CURRENT_USER &#40; Transact-SQL &#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [Функция SESSION_USER &#40; Transact-SQL &#41;](../../t-sql/functions/session-user-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [Функция SYSTEM_USER &#40; Transact-SQL &#41;](../../t-sql/functions/system-user-transact-sql.md)  
  
  

