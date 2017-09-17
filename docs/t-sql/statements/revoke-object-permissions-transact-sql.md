---
title: "REVOKE, Отмена разрешения (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table permissions [SQL Server], revoking
- REVOKE statement, objects
- revoking permissions to access tables
- object permissions [SQL Server], revoking
ms.assetid: 99c7146e-d2e7-4f1a-80ff-21a05bc5e8bb
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c8895f85a3484258ee68f40e8d2261206fd16d0a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-object-permissions-transact-sql"></a>REVOKE, отмена разрешения (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет разрешения на таблицу, представление, возвращающую табличное значение функцию, хранимую процедуру, расширенную хранимую процедуру, скалярную функцию, агрегатную функцию, очередь обслуживания или синоним. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE [ GRANT OPTION FOR ] <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        { FROM | TO } <database_principal> [ ,...n ]   
    [ CASCADE ]  
    [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login      
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Указывает разрешение, которое может быть отменено для содержащегося в схеме объекта. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 ALL  
 Отмена ALL не отменяет все возможные разрешения. Отмена ALL эквивалентна отмене всех разрешений [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92, применимых к указанному объекту. Значение ALL различается для разных типов объектов  
  
 Разрешения на скалярные функции: выполнение, ссылается на.  
  
 Табличная функция разрешения: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
 Разрешения на хранимые процедуры: выполнение.  
  
 Таблица разрешения: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
 Просмотр разрешений: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
 PRIVILEGES  
 Включено для обеспечения совместимости с [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92. Не изменяет работу ALL.  
  
 *столбец*  
 Указывает имя столбца в таблице, представлении или функции с табличным значением, для которого отменяется разрешение. Круглые скобки не требуются. Для столбца можно запрещать только разрешения SELECT, REFERENCES и UPDATE. *столбец* может быть указан в предложении permissions или после имени защищаемого объекта.  
  
 ON [ОБЪЕКТА::] [ *schema_name* ]. *object_name*  
 Указывает объект, для которого отменяется разрешение. Фраза OBJECT необязательна Если *schema_name* указано. Если ЖЕ она указана, требуется квалификатор области (::). Если *schema_name* не указан, используется схема по умолчанию. Если *schema_name* указано, требуется квалификатор области схемы (.).  
  
 {ИЗ | К} \<database_principal > Указывает участника, от которого отменяется разрешение.  
  
 GRANT OPTION  
 Показывает, что отменяется право на предоставление указанного разрешения другим участникам. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS \<database_principal > Указывает участника, от которого участник, выполняющий данный запрос, наследует право отмены разрешения.  
  
 *Пользователь_базы_данных*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Замечания  
 Сведения об объектах доступны через различные представления каталога. Дополнительные сведения см. в разделе [представления каталога объектов &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md).  
  
 Объект является защищаемым на уровне схемы. Он содержится в схеме, которая является его родителем в иерархии разрешений. Наиболее специфичные и ограниченные разрешения объекта, которые можно отменить, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение объекта|Содержится в разрешении объекта|Содержится в разрешении схемы|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|DELETE|CONTROL|DELETE|  
|Выполните|CONTROL|Выполните|  
|INSERT|CONTROL|INSERT|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL для данного объекта.  
  
 При использовании предложения AS указанный участник должен быть владельцем объекта, разрешения на который отменяются.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-revoking-select-permission-on-a-table"></a>A. Отмена разрешения SELECT для таблицы  
 Следующий пример отменяет разрешение `SELECT` у пользователя `RosaQdM` для таблицы `Person.Address` в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
REVOKE SELECT ON OBJECT::Person.Address FROM RosaQdM;  
GO  
```  
  
### <a name="b-revoking-execute-permission-on-a-stored-procedure"></a>Б. Отмена разрешения EXECUTE для хранимой процедуры  
 Следующий пример отменяет разрешение `EXECUTE` для хранимой процедуры `HumanResources.uspUpdateEmployeeHireInfo` у роли приложения с именем `Recruiting11`.  
  
```  
USE AdventureWorks2012;  
REVOKE EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    FROM Recruiting11;  
GO   
```  
  
### <a name="c-revoking-references-permission-on-a-view-with-cascade"></a>В. Отмена разрешения REFERENCES для представления с CASCADE  
 Следующий пример отменяет разрешение `REFERENCES` для столбца `BusinessEntityID` в представлении `HumanResources.vEmployee` у пользователя `Wanida` с `CASCADE`.  
  
```  
USE AdventureWorks2012;  
REVOKE REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    FROM Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на объект (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [DENY, предоставление разрешений на объект (Transact-SQL)](../../t-sql/statements/deny-object-permissions-transact-sql.md)   
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  

