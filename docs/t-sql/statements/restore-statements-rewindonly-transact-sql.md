---
title: RESTORE REWINDONLY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- RESTORE_REWINDONLY_TSQL
- RESTORE REWINDONLY
dev_langs:
- TSQL
helpviewer_keywords:
- closing backup devices
- backup devices [SQL Server], rewinding
- media [SQL Server]
- open back devices
- rewinding backup devices
- RESTORE REWINDONLY statement
ms.assetid: 7f825b40-2264-4608-9809-590d0f09d882
caps.latest.revision: 50
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 486715799d2fee564c51336bd958eb603cd1b490
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038662"
---
# <a name="restore-statements---rewindonly-transact-sql"></a>Инструкции RESTORE — REWINDONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перематывает на начало и закрывает указанное ленточное устройство, если оно осталось открытым после выполнения инструкции BACKUP или RESTORE без аргумента NOREWIND. Эта команда поддерживается только для ленточных устройств.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RESTORE REWINDONLY   
FROM <backup_device> [ ,...n ]  
[ WITH {UNLOAD | NOUNLOAD}]  
}   
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | TAPE = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}   
```  
  
## <a name="arguments"></a>Аргументы  
 **\<backup_device> ::=** 
  
 Логическое или физическое устройство резервного копирования.  
  
 { *logical_backup_device_name* | **@***logical_backup_device_name_var* } Логическое имя устройства резервного копирования, из которого восстанавливается база данных. Это имя создается с помощью процедуры **sp_addumpdevice** и должно соответствовать правилам наименования идентификаторов. Если аргумент задается в виде переменной (**@***logical_backup_device_name_var*), имя устройства резервного копирования можно указать как строковую константу (**@***logical_backup_device_name_var* = *logical_backup_device_name*) или как переменную любого строкового типа данных, за исключением типов данных **ntext** или **text**.  
  
 {DISK | TAPE } **=** { **'***physical_backup_device_name***'** | **@***physical_backup_device_name_var* } Разрешает восстановление резервных копий с именованного диска или ленточного устройства. Типы дисковых и ленточных устройств должны быть заданы с реальным именем устройства (например, полный путь и имя файла): DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL\BACKUP\Mybackup.bak' или TAPE = '\\\\.\TAPE0'. Если аргумент задается в виде переменной (**@***physical_backup_device_name_var*), имя устройства можно указать как строковую константу (**@***physical_backup_device_name_var* = '* physcial_backup_device_name*') или как другую переменную любого строкового типа данных, за исключением типов данных **ntext** или **text**.  
  
 Укажите тип дискового устройства с помощью сетевого сервера с именем UNC (которое должно содержать имя компьютера). Дополнительные сведения об именах UNC см. в разделе [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 Для выполнения операции RESTORE учетная запись, с помощью которой был запущен Microsoft SQL Server, должна иметь доступ типа READ к удаленному компьютеру или серверу.  
  
 *n*  
 Заполнитель, указывающий на наличие нескольких устройств резервного копирования, а также на возможность задать логическое устройство резервного копирования. Максимальное число устройств резервного копирования или логических устройств резервного копирования равно **64**.  
  
 Необходимость наличия при восстановлении того же количества устройств резервного копирования, какое было использовано для создания набора носителей (которым принадлежат резервные копии), зависит от режима восстановления. Восстановление в сети позволяет использовать меньше устройств, чем было задействовано при создании резервных копий. При восстановлении в сети обязательно наличие всех устройств резервного копирования. Попытка выполнить восстановление с меньшим числом устройств не будет успешно завершена.  
  
 Дополнительные сведения см. в разделе [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
> [!NOTE]  
>  Восстанавливая резервные копии с зеркального набора носителей, можно указать по одному зеркалу для каждого семейства носителей. Но в случае возникновения ошибок наличие других зеркал способствует быстрому устранению некоторых неполадок при восстановлении. Поврежденный том носителя можно заменить соответствующим томом с другого зеркала. Обратите внимание, что для восстановления вне сети можно использовать меньше устройств, чем семейств носителей, однако каждое семейство обрабатывается только один раз.  
  
 **Параметры инструкции WITH**  
  
 UNLOAD  
 Означает автоматическую перемотку и выгрузку ленты по завершении инструкции RESTORE. При запуске нового сеанса пользователя выполнение параметра UNLOAD задано по умолчанию. Оно остается заданным до тех пор, пока не будет задан параметр NOUNLOAD. Этот параметр применяется только с ленточными устройствами. Если при выполнении инструкции RESTORE используется другой тип устройств резервного копирования, то этот параметр не учитывается.  
  
 NOUNLOAD  
 Указывает, что по выполнении инструкции RESTORE лента из ленточного устройства автоматически не выгружается. NOUNLOAD остается установленным до тех пор, пока указано UNLOAD.  
  
## <a name="general-remarks"></a>Общие замечания  
 Инструкция RESTORE REWINDONLY является альтернативой инструкции RESTORE LABELONLY FROM TAPE = \<name> WITH REWIND. Список открытых ленточных устройств можно получить из динамического административного представления [sys.dm_io_backup_tapes](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Инструкцию RESTORE REWINDONLY может выполнять любой пользователь.  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

