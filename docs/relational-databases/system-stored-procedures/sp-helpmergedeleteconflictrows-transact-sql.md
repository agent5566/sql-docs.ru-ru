---
title: sp_helpmergedeleteconflictrows (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 270ca534b5527efa9dea52b107166bb445965b2f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595682"
---
# <a name="sphelpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о строках данных, утративших конфликты удаления. Эта хранимая процедура выполняется в базе данных публикации на издателе или в базе данных подписки на подписчике при использовании децентрализованной регистрации конфликтов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию **%**. Если указана публикация, возвращаются все конфликты, определенные этой публикацией.  
  
 [  **@source_object=**] **"***source_object***"**  
 Имя исходного объекта. *source_object* — **nvarchar(386)**, значение по умолчанию NULL.  
  
 [  **@publisher=**] **"***издателя***"**  
 — Имя издателя. *издателя* — **sysname**, значение по умолчанию NULL.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 — Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию NULL.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar(386)**|Исходный объект для конфликта удаления.|  
|**столбец ROWGUID**|**uniqueidentifier**|Идентификатор строки для конфликта удаления.|  
|**conflict_type**|**int**|Код, указывающий на тип конфликта.<br /><br /> **1** = UpdateConflict: конфликт обнаружен на уровне строк.<br /><br /> **2** = ColumnUpdateConflict: конфликт обнаружен на уровне столбца.<br /><br /> **3** = UpdateDeleteWinsConflict: конфликт разрешен удалением.<br /><br /> **4** = UpdateWinsDeleteConflict: удаленный идентификатор rowguid, которая уступает в конфликте, записывается в этой таблице.<br /><br /> **5** = UploadInsertFailed: инструкция Insert от подписчика не может быть применена на издателе.<br /><br /> **6** = DownloadInsertFailed: инструкция Insert от издателя не может быть применена на подписчике.<br /><br /> **7** = UploadDeleteFailed: Delete на подписчике не удалось загрузить на издатель.<br /><br /> **8** = DownloadDeleteFailed: не удалось загрузить удаления со стороны издателя на подписчик.<br /><br /> **9** = UploadUpdateFailed: обновления на подписчике не может быть применена на издателе.<br /><br /> **10** = DownloadUpdateFailed: не удалось применить обновления со стороны издателя на подписчик.|  
|**reason_code**|**Int**|Код ошибки, который может зависеть от контекста.|  
|**reason_text**|**varchar(720)**|Описание ошибки, которое может зависеть от контекста.|  
|**origin_datasource**|**varchar(255)**|Источник конфликта.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**MSrepl_create_time**|**datetime**|Время, когда были добавлены сведения о конфликте.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergedeleteconflictrows** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_helpmergedeleteconflictrows**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
