---
title: Свойства задания — создание задания (страница "Расписания") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 33c6b21edd53eb4c362144ed6ae84e8651b9b201
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853312"
---
# <a name="job-properties---new-job-schedules-page"></a>Свойства задания — новое задание (страница "Расписания")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница позволяет просматривать и организовывать расписания для задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
**Список расписаний**  
Список расписаний для данного задания.  
  
**Создать**  
Создает новое расписание. После создания нового расписания оно добавляется к заданию.  
  
**Выбрать**  
Выбор расписания из существующих расписаний. Поскольку у задания и расписания должен быть один и тот же владелец, здесь можно выбирать только из расписаний, которыми владеете.  
  
**Изменить**  
Изменяет выбранное расписание задания.  
  
**Удалить**  
Удалить выбранное расписание из задания. Если больше ни одно задание не использует это расписание, оно удаляется из базы данных.  
  
## <a name="see-also"></a>См. также:  
[Реализация заданий](../../ssms/agent/implement-jobs.md)  
  
