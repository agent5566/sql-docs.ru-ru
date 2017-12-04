---
title: "syspolicy_policy_execution_history (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs: TSQL
helpviewer_keywords: syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90d0de71b9f93bb264dea3b9562a3d9bfa44669c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает время выполнения политик, результат каждого выполнения и сведения об ошибках, возникших при выполнении. Следующая таблица описывает столбцы в представлении syspolicy_policy_execution_history.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Идентификатор записи. Каждая запись указывает на политику и время ее выполнения.|  
|policy_id|**int**|Идентификатор политики.|  
|start_date|**datetime**|Дата и время последней попытки запуска политики.|  
|end_date|**datetime**|Время, когда политика закончила выполняться.|  
|набор по|**bit**|Успешность или неуспешность выполнения политики. 0 = неуспешное завершение, 1 = успешное завершение.|  
|exception_message|**nvarchar(max)**|Сообщение, выданное в результате возникшего исключения.|  
|exception|**nvarchar(max)**|Описание возникшего исключения.|  
  
## <a name="remarks"></a>Замечания  
 [Syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) содержит подробности, связанные с целевыми объектами политик и проверенными выражениями, задающими.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  