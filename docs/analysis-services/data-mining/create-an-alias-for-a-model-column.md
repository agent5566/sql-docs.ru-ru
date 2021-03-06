---
title: Создать псевдоним для столбца модели | Документы Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c7f7a6139adb75c9a041238e4c8f911bb88ff711
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019101"
---
# <a name="create-an-alias-for-a-model-column"></a>создать псевдоним для столбца модели
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]для столбца модели можно создать псевдоним. Необходимость в этом может возникнуть, если имя структуры интеллектуального анализа данных имеет слишком большую длину и с ним неудобно работать, или если необходимо присвоить столбцу другое имя, более точно описывающее его содержимое или назначение в модели. Например, если создается копия столбца структуры, а затем дискретизация столбца выполняется различно для конкретной модели, можно переименовать столбец, чтобы его имя более точно отражало его содержимое.  
  
 Чтобы создать псевдоним для столбца модели, можно воспользоваться панелью **Свойства** и задать свойство [Name](../../analysis-services/scripting/properties/name-element-assl.md) столбца.  
  
 На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных псевдоним отображается в круглых скобках рядом с меткой использования столбца.  
  
 Дополнительные сведения о задании свойств в модели интеллектуального анализа данных см. в разделе [Столбцы модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Добавление псевдонима к столбцу модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных щелкните правой кнопкой мыши ячейку в модели интеллектуального анализа данных для столбца интеллектуального анализа, которую необходимо изменить, и выберите пункт **Свойства**.  
  
2.  В окне **Свойства** в правой части экрана щелкните ячейку рядом со свойством Name и удалите текущее значение. Введите новое имя столбца.  
  
## <a name="see-also"></a>См. также  
 [Задачи модели интеллектуального анализа данных и инструкции](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Свойства модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-properties.md)  
  
  
