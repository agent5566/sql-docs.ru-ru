---
title: Элемент OverrideBehavior (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OverrideBehavior Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- OverrideBehavior element
ms.assetid: 6a5b361a-6061-4b73-b1a7-1237fb77606c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 88cf3dd287e1b55fee5377e2238d4d7c738cfe16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203624"
---
# <a name="overridebehavior-element-assl"></a>Элемент OverrideBehavior (ASSL)
  Указывает на переопределения связи, описываемого [AttributeRelationship](../objects/attributerelationship-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <OverrideBehavior>...</OverrideBehavior>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Strong*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `OverrideBehavior` определяет, как позиционирование связанного атрибута влияет на позиционирование самого атрибута.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Strong*|Указывает на переопределения связи, задаваемой элементом AttributeRelationship. Указывает, как позиционирование одного атрибута влияет на позицию другого.|  
|*None*|Не влияет.|  
  
 Перечисление, соответствующее допустимым значениям элемента `OverrideBehavior` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.OverrideBehavior>.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
