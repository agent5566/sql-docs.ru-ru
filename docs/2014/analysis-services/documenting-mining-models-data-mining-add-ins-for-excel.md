---
title: Документирование моделей интеллектуального анализа данных (надстройки интеллектуального анализа для Excel данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6f605fd2ef1e0aafad5b34a2b74c12fc95be6ef7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167715"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a>Документирование моделей интеллектуального анализа данных (надстройки интеллектуального анализа данных для Excel)
  ![Кнопка модель документа, интеллектуального анализа данных](media/dmc-docmodel.gif "кнопка модели документов, интеллектуального анализа данных")  
  
 **Модели документов** мастер создает отчет, который предоставляет полезные сведения о моделях интеллектуального анализа данных, которые вы создали. При помощи документирования созданной модели можно отслеживать источник данных, используемых для формирования модели, получать дополнительные сведения о времени обработки модели и отслеживать изменения параметров, влияющие на результаты модели.  
  
## <a name="using-the-document-model-wizard"></a>Использование мастера документирования модели  
  
1.  Нажмите кнопку **интеллектуального анализа данных** вкладки.  
  
2.  В **использование модели** щелкните **модели документов**.  
  
3.  В **Выбор модели** диалоговом окне выберите модель, для которой отчет и нажмите кнопку **Далее**. Необходимо запустить **модели документов** мастер отдельно для каждой модели, которую необходимо документировать.  
  
4.  В **выбрать сведения о документации** диалоговое окно, выберите один из двух вариантов: **заполните сведения** или **сводные данные**.  
  
5.  Нажмите кнопку **Готово**.  
  
6.  Мастер автоматически создаст новый лист, содержащий указанный отчет с названием **документации по модели**,  
  
## <a name="understanding-the-report"></a>Основные сведения об отчете  
 Создавая отчет, документирующий модель интеллектуального анализа данных, можно создать как сводку, содержащую основные сведения — имя и описание модели, так и полный отчет, содержащий сведения о лежащей в основе структуре и расширенные сведения о модели интеллектуального анализа данных.  
  
 В зависимости от алгоритма, использованного для создания модели, предоставляются различные типы данных. Например, в модели взаимосвязей пользователи будут заинтересованы в сведениях о числе наборов элементов и о числе сформированных правил. В модели кластеризации больший интерес будет предоставлять число кластеров.  
  
 В следующей таблице перечисляются параметры и сведения, предоставляемые в отчете для каждого параметра.  
  
> [!NOTE]  
>  По умолчанию для столбцов в отчете устанавливается определенный размер. Следовательно, если имена столбцов или значения имеют слишком большую длину, то они могут быть скрыты или могут быть отображены в Excel как серия символов ###. Чтобы отобразить значения, следует изменить размер строки. Если ячейка выбрана, то для отображения полного значения или строки можно щелкнуть и перетащить двойные стрелки на правом крае строки формул.  
  
### <a name="summary-report"></a>Сводный отчет  
  
||||  
|-|-|-|  
|**Метаданные**|Имя модели<br /><br /> Описание модели<br /><br /> Имя алгоритма<br /><br /> Дата последней обработки||  
|**Результаты модели**|Взаимосвязь|Число наборов элементов<br /><br /> Число правил|  
||Кластеризация|Число кластеров<br /><br /> Несущее множество каждого кластера|  
||Дерево решений|Количество деревьев<br /><br /> Количество узлов в каждом дереве|  
||Линейная регрессия|Количество деревьев (всегда 1)<br /><br /> Количество узлов (всегда 1)|  
||Упрощенный алгоритм Байеса|Важные атрибуты|  
||Нейронная сеть|Количество входных узлов<br /><br /> Количество выходных узлов<br /><br /> Количество скрытых узлов|  
||Кластеризация последовательностей|Количество кластеров|  
  
### <a name="complete-report"></a>Полный отчет  
 В полный отчет включаются все данные, содержащиеся в сводном отчете, а также подробные сведения о столбцах данных, использованных в модели, и результаты анализа.  
  
||||  
|-|-|-|  
|**Метаданные**|Метаданные модели|Параметры и значения алгоритма|  
||Метаданные столбца|Имя столбца<br /><br /> Использование<br /><br /> Тип данных<br /><br /> Тип содержимого<br /><br /> Значения (список дискретных значений или диапазон значений)|  
|**Статистики модели**|Непрерывные столбцы|Среднее значение<br /><br /> Минимальное значение<br /><br /> Максимальное значение<br /><br /> Корень среднеквадратичной погрешности<br /><br /> Средняя абсолютная погрешность<br /><br /> Логарифмическая оценка<br /><br /> Формула регрессии (только для моделей с линейной регрессией)|  
||Дискретные столбцы|Число передач<br /><br /> Число сбоев<br /><br /> Логарифмическая оценка<br /><br /> Точность прогноза|  
  
> [!NOTE]  
>  Документировать можно любой тип модели, поддерживаемый службами SQL Server Analysis Services. Следовательно, в таблице перечисляются некоторые типы моделей, которые не могут быть созданы с помощью средств анализа таблиц или с помощью мастеров клиента интеллектуального анализа данных. Тем не менее, можно создать все типы моделей с помощью **расширенный редактор запросов интеллектуального анализа данных**. Дополнительные сведения см. в разделе [запроса &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание и масштабирование моделей интеллектуального анализа данных &#40;интеллектуального анализа данных надстройки для Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  