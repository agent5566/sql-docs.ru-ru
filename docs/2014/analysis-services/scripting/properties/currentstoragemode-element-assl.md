---
title: Элемент CurrentStorageMode (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CurrentStorageMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CurrentStorageMode
helpviewer_keywords:
- CurrentStorageMode element
ms.assetid: 050c21e4-368b-4ff0-b0c5-349f93fe9747
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d930292898f55736daea9e00893cd6e5f000a34
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058774"
---
# <a name="currentstoragemode-element-assl"></a>Элемент CurrentStorageMode (ASSL)
  Определяет текущий режим хранения для родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension> <!-- or Partition -->  
   <CurrentStorageMode>...</CurrentStorageMode>  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*ROLAP*|  
|Количество элементов|0—1: необязательный элемент, который может встречаться один раз или вообще не встречаться.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Измерение](../objects/dimension-element-assl.md), [секции](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `CurrentStorageMode` определяет режим хранения, который используется в настоящее время для упреждающего кэширования и применим ко всем атрибутам родительского элемента.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*MOLAP*|Родительский элемент использует многомерное хранилище OLAP (MOLAP).|  
|*ROLAP*|Родительский элемент использует реляционное хранилище OLAP (ROLAP).|  
|*HOLAP*|Родительский элемент использует гибридное хранилище OLAP (HOLAP). **Примечание:** это значение допустимо только для [секции](../objects/partition-element-assl.md) родительскими элементами.|  
  
 Перечислением, относящимся к разрешенным значениям `CurrentStorageMode` в модели объектов AMO является <xref:Microsoft.AnalysisServices.StorageMode>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
