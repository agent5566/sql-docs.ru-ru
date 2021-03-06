---
title: Набор строк DISCOVER_OBJECT_MEMORY_USAGE | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cfea97bbc901c86c5c90a72b74d9ddba396e745c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126554"
---
# <a name="discoverobjectmemoryusage-rowset"></a>Набор строк DISCOVER_OBJECT_MEMORY_USAGE
  Предоставляет сведения об использовании ресурсов памяти объектами.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_OBJECT_MEMORY_USAGE` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`||Путь к родительскому объекту для текущего объекта.|  
|`OBJECT_ID`|`DBTYPE_WSTR`||Идентификатор объекта, определенный при создании.|  
|`OBJECT_MEMORY_SHRINKABLE`|`DBTYPE_I8`||Общий объем памяти (в байтах), который используется всеми сжимаемыми объектами, непосредственно принадлежащими текущему объекту. В это значение не включается память объектов, принадлежащих именованным объектам, которые в свою очередь принадлежат текущему объекту.|  
|`OBJECT_MEMORY_NONSHRINKABLE`|`DBTYPE_I8`||Объем памяти (в байтах) всех несжимаемых объектов, которые принадлежат напрямую текущему объекту. В это значение не включается память объектов, принадлежащих именованным объектам, которые в свою очередь принадлежат текущему объекту.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Номер версии метаданных объекта. Этот номер изменяется при каждом изменении объекта.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Номер журнала обращений и преобразований для данных в объекте. Этот номер увеличивается каждый раз при обработке объекта.|  
|`OBJECT_TYPE_ID`|`DBTYPE_I4`||Зарезервировано для внутреннего использования.|  
|`OBJECT_TIME_CREATED`|`DBTYPE_DBTIMESTAMP`||Время сервера в формате UTC, когда был создан объект.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_OBJECT_MEMORY_USAGE` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`OBJECT_ID`|`DBTYPE_WSTR`|Необязательно|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
