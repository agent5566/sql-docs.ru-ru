---
title: Элемент Usage (MiningModelColumn) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Usage Element (MiningModelColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 220f59e5e342f61f30d0f94bc9f9728982105986
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090310"
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Элемент Usage (MiningModelColumn) (ASSL)
  Описывает как связанный столбец в родительском объекте [MiningStructure](../objects/miningstructure-element-assl.md) используется.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Key*|Столбец является ключевым.|  
|*Входные данные*|Столбец является входным.|  
|*Predict*|Столбец является столбцом прогноза.|  
|*PredictOnly*|Столбец является только столбцом прогноза.|  
|*None*|Столбец не используется этой моделью. **Предупреждение:** при Usage имеет значение «None», службы Analysis Services не отправляют никакого значения сервера по умолчанию; таким образом, атрибут Usage не включается в запрос/ответ.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Usage` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
