---
title: Release Notes (драйвер OLE DB для SQL Server) | Документация Майкрософт
ms.date: 07/03/2018
ms.prod: sql
ms.suite: sql
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
ms.openlocfilehash: ec5abfce888f0af956f1b72f509ef298ee7405a0
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109376"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Заметки о выпуске Microsoft OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

На этой странице описаны, что был добавлен в каждую версию драйвера Microsoft OLE DB для SQL Server.

## <a name="whats-new-in-version-1810"></a>Новые возможности версии 18.1.0

**Функции, добавленные:**

* Поддержка `UseFMTONLY` ключевое слово строки подключения и `SSPROP_INIT_USEFMTONLY` свойство инициализации.
`UseFMTONLY` Определяет, как метаданные извлекаются при соединении с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях.  
Дополнительные сведения см. в разделе:
  * [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)

**Ошибки, исправленные:**

* Фиксированный неправильная версия файла формата BCP. Неправильно 18.0 драйвера OLE DB задает версию файла формата BCP 18.0 вместо 11.0. Формат файлов, создаваемых 18.0 драйвера OLE DB не может быть прочитан 18.1 драйвера OLE DB. Если вам нужно использовать файлы форматирования, созданный в предыдущей версии драйвера с помощью нового драйвера, можно вручную изменить файлы, чтобы изменить версию 11.0.

## <a name="whats-new-in-version-1802"></a>Новые возможности версии 18.0.2

**Функции, добавленные**:

* Поддержка `MultiSubnetFailover` ключевое слово строки подключения и `SSPROP_INIT_MULTISUBNETFAILOVER` свойство инициализации.  
Дополнительные сведения см. в разделе:  
  * [Поддержка высокого уровня доступности и аварийного восстановления в драйвере OLE DB для SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
  * [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)

## <a name="see-also"></a>См. также раздел
[Драйвер Microsoft OLE DB для SQL Server](oledb-driver-for-sql-server.md)
