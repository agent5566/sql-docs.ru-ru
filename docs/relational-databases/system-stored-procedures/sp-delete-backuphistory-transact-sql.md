---
title: "sp_delete_backuphistory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_backuphistory
- sp_delete_backuphistory_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_backuphistory
ms.assetid: bdb56834-616e-47e4-b942-e895d2325e97
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3e45359c1c38684e5d197e81295af0ede11cfe3a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spdeletebackuphistory-transact-sql"></a>sp_delete_backuphistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Уменьшает размер таблиц журнала резервного копирования и восстановления, удаляя записи для резервных наборов данных, которые старше указанной даты. Дополнительные строки добавляются резервного копирования и восстановления таблицы журнала после создания каждой резервной копии или выполнении операции восстановления; Поэтому рекомендуется периодически выполнять **sp_delete_backuphistory**.  
  
> [!NOTE]  
>  Таблицы журнала резервного копирования и восстановления находятся в **msdb** базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_backuphistory [ @oldest_date = ] 'oldest_date'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@oldest_date=** ] **"***oldest_date***"**  
 Самая ранняя дата, сохраненная в таблицах журнала резервного копирования и восстановления. *oldest_date* — **datetime**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_backuphistory** должна запускаться из **msdb** базы данных и влияет на следующие таблицы:  
  
-   [backupfile;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
  
-   [backupmediafamily;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
  
-   [backupmediaset;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
  
-   [backupset;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [restorefile;](../../relational-databases/system-tables/restorefile-transact-sql.md)  
  
-   [restorefilegroup;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
  
-   [restorehistory.](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
  
 Физические файлы резервных копий сохраняются, даже если удаляется весь журнал.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **sysadmin** предопределенной роли сервера, но разрешения могут предоставляться другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере из таблиц журнала резервного копирования и восстановления удаляются все записи, внесенные до 12:00 14 января 2010 года.  
  
```  
USE msdb;  
GO  
EXEC sp_delete_backuphistory @oldest_date = '01/14/2010';  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_database_backuphistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  