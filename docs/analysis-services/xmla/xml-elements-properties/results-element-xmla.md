---
title: результаты Element (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7fc64d6b31f1b05d8bf5b4d1c80d75dff0583e86
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968666"
---
# <a name="results-element-xmla"></a>Элемент results (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию элементов [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) , возвращаемых методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) с использованием команды [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) .  
  
 **Пространство имен** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[вернуть](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Дочерние элементы|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Если команда **Batch** выполняется методом **Execute** , то элемент **return** содержит единственный элемент **results** , а не единственный элемент **root** . Содержимое элемента **results** зависит от параметров, используемых для выполнения команды **Batch** .  
  
 Применительно к командам **Batch** , не входящим в состав транзакции, элемент **results** содержит по одному элементу **root** для каждой команды, выполненной этой командой **Batch** , независимо от того, завершается ли эта команда успешно или неудачно. Применительно к командам **Batch** , входящим в состав транзакции, элемент **results** содержит только один элемент **root** , который содержит информацию об ошибке для команды **Batch** , завершившейся неудачей в составе команды.  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
