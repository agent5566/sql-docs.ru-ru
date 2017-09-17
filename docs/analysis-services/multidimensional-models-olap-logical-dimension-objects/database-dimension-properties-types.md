---
title: "Типы измерений | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5fa77532b4c674c4b5035cf6b591b973008ae6e5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimension-properties---types"></a>Свойства измерения базы данных - типы
  **Тип** предоставляет сведения о содержимом измерения серверу и клиентским приложениям. В некоторых случаях **тип** параметр содержит рекомендации для клиентских приложений и является необязательным. В других случаях таких как **учетные записи** или **время** измерений, **тип** параметры свойств для измерения и его атрибутов определяет конкретные режимы, серверные и могут быть востребованы для реализации определенных режимов куба. Например **тип** свойство измерения можно присвоить значение **учетные записи** для указания для клиентских приложений, что в стандартном измерении содержатся атрибуты счетов. Дополнительные сведения о времени, счетов и измерение валюты см. в разделе [Создание измерения типа Date](../../analysis-services/multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [создания учетной записи Finance измерением типа родители потомки](../../analysis-services/multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), и [создать валюты Тип измерения](../../analysis-services/multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 Значение по умолчанию для типа измерения — **регулярного**, что не дает представления о содержимом измерения. Это значение по умолчанию для всех измерений при первоначальном определении измерения, если не указать **время** при определении измерения с помощью мастера измерений. Необходимо также оставить **регулярного** как тип измерения, если мастер измерений не включает соответствующих типов для типа измерения.  
  
## <a name="available-dimension-types"></a>Доступные типы измерений  
 В следующей таблице описаны типы измерения, доступные в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Тип измерения|Description|  
|--------------------|-----------------|  
|Regular|Измерение, тип которого не был изменен на специальный тип измерения. |  
|Time|Измерение, атрибуты которого представляют периоды времени, например годы, семестры, кварталы, месяцы и дни.|  
|Organization|Измерение, атрибуты которого представляют сведения об организации, например сотрудниках или филиалах.|  
|Geography|Измерение, атрибуты которого представляют географические сведения, например города или почтовые индексы.|  
|BillOfMaterials|Измерение, атрибуты которого представляют сведения по описи или производственные данные, например списки деталей для изделий.|  
|Измерение счетов|Измерение, атрибуты которого представляют диаграмму счетов для финансовой отчетности.|  
|Заказчики|Измерение, атрибуты которого представляют сведения о заказчиках или контактные данные.|  
|Измерение продуктов|Измерение, атрибуты которого представляют сведения о продуктах.|  
|Сценарий|Измерение, атрибуты которого представляют сведения о планах или данные о стратегическом анализе.|  
|Количественное измерение|Измерение, атрибуты которого представляют количественные данные.|  
|Служебная программа|Измерение, атрибуты которого представляют прочие сведения.|  
|Измерение валют|Измерение, атрибуты которого содержат данные валюты и метаданные.|  
|Изменения курсов|Измерение, атрибуты которого представляют данные о курсе обмена валюты.|  
|Channel|Измерение, атрибуты которого представляют данные о каналах.|  
|Promotion|Измерение, атрибуты которого представляют сведения об акциях по продвижению.|  
  
## <a name="see-also"></a>См. также:  
 [Создать измерение с помощью существующей таблицы](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Измерения (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  