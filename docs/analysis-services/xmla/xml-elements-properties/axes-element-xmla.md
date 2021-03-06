---
title: Осей элемент (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a8dfff1c8a551157661bcb1de5700bf51a7f914
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038022"
---
# <a name="axes-element-xmla"></a>Элемент Axes (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию [оси](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) элементов, представляющих данные оси, содержащиеся в [корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемент, использующий [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) тип данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <Axes>  
      <Axis>...</Axis>  
   </Axes>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Любой|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Дочерние элементы|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 В разделе **осей** элемент, **оси** элементы перечисляются в порядке их появления в наборе данных, начиная с нуля. **AxisFormat** определяет параметр свойства XMLA как **оси** должны быть отформатированы элементы. Дополнительные сведения о **AxisFormat** свойство, см. в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Ось представляет набор кортежей, в котором все кортежи набора имеют одну и ту же размерность. Набор может быть представлен с помощью разных способов, позволяющих достичь разных преимуществ. Например, следующий набор из четырех кортежей может быть представлен в виде коллекций двумерных кортежей или декартова произведения двух одномерных наборов.  
  
|1999|1999|2000|2000|  
|----------|----------|----------|----------|  
|Actual|Budget|Actual|Budget|  
  
 Этот набор кортежей может быть представлен также, как коллекция двумерных кортежей:  
  
```  
{ ( 1999, Actual ), ( 1999, Budget ), ( 2000, Actual ), ( 2000, Budget ) }  
```  
  
 Этот набор кортежей может быть представлен, как декартово произведение двух одномерных наборов:  
  
```  
{ 1999, 2000 } x { Actual, Budget }  
```  
  
 Первое представление, в котором используются двумерные кортежи, является более простым с точки зрения использования клиентских инструментов. А во втором представлении, основанном на декартовом произведении одномерных наборов, используется меньше пространства и сохраняется многомерный характер набора.  
  
 В следующей таблице перечислены операции, которые могут использоваться для определения и описания характеристик структуры и членов оси.  
  
|Операция|Описание|  
|---------------|-----------------|  
|Член|Наименьшая единица измерения на оси, представляющая элемент в иерархии измерений.|  
|Члены|Коллекция **член** объектов с использованием того же иерархии измерений.|  
|Кортеж|Коллекция элементов из разных иерархий измерений.|  
|Кортежи|Коллекция **кортежа** объектов одинаковой размерности.|  
|Union|Объединение наборов.|  
|CrossJoin|Декартово произведение наборов.|  
  
 В этих операциях производится преобразование двумерных кортежей и декартова произведения одномерных наборов следующим образом.  
  
## <a name="two-dimensional-tuples"></a>Двумерные кортежи  
  
```  
Tuples (  
   Tuple( Member(1999), Member(Actual) ),  
   Tuple( Member(1999), Member(Budget) ),  
   Tuple( Member(2000), Member(Actual) ),  
   Tuple( Member(2000), Member(Budget) )  
```  
  
## <a name="cartesian-product-of-one-dimensional-sets"></a>Декартово произведение одномерных наборов  
  
```  
CrossProduct (  
   Members( Member(1999), Member(2000) ),  
   Members( Member(Actual), Member(Budget) )  
```  
  
 Клиент может использовать **AxisFormat** свойство для затребования конкретного представления.  
  
## <a name="see-also"></a>См. также
 [Тип данных MDDataSet &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
