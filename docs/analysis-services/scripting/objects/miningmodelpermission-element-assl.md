---
title: "Элемент MiningModelPermission (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningModelPermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2cd366179355590dca84fb84f8a00e8dfc103a3f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="miningmodelpermission-element-assl"></a>Элемент MiningModelPermission (ASSL)
  Определяет разрешения членов [роли](../../../analysis-services/scripting/objects/role-element-assl.md) имеют для отдельных [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelPermissions>  
   <MiningModelPermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <AllowBrowsing>...</AllowBrowsing>  
   </MiningModelPermission>  
</MiningModelPermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)|  
|Дочерние элементы|[AllowBrowsing](../../../analysis-services/scripting/properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], можно включить детализацию в структурах интеллектуального анализа данных, добавив **AllowDrillthrough** право [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) коллекции. Если **AllowDrillthrough** включен в структуре интеллектуального анализа данных и модели интеллектуального анализа данных, любой член роли, имеющей [элемент AllowDrillThrough &#40; ASSL &#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) для модели разрешения запросов к модели интеллектуального анализа данных и возвращать столбцы структуры, которые не были включены в модель, используя следующий синтаксис:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Поэтому, чтобы защитить конфиденциальные или персональные данные, разрешение **AllowDrillthrough** для модели интеллектуального анализа данных следует предоставлять только при необходимости. Дополнительные сведения см. в разделе [AllowDrillThrough, элемент &#40; ASSL &#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  