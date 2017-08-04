---
title: "NonEmptyCrossjoin (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NONEMPTYCROSSJOIN
dev_langs:
- kbMDX
helpviewer_keywords:
- NonEmptyCrossjoin function
ms.assetid: 3dc9522d-9126-4f7a-b587-216fa7a06c62
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 54ea9a17d94b73d5423384023d49e4c86771f072
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает набор, содержащий перекрестное произведение двух или нескольких наборов, исключая пустые кортежи и кортежи, не связанные с данными таблиц фактов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество наборов, которые необходимо вернуть.  
  
## <a name="remarks"></a>Замечания  
 **NonEmptyCrossjoin** функция возвращает перекрестное произведение двух или более множеств в виде одного множества, исключая пустые кортежи и кортежи без данных, предоставленных базовым таблицам фактов. Специфика **NonEmptyCrossjoin** работы функции все вычисляемые элементы автоматически исключаются.  
  
 Если *число* не указан, функция выполняет перекрестное соединение всех указанных наборов и исключает из полученного набора пустые элементы. В противном случае функция выполняет перекрестное соединение указанного количества наборов, начиная с первого. **NonEmptyCrossjoin** функция использует остальные наборы, которые заданы в последующих указанных наборов, но которые не были перекрестного присоединены, чтобы определить, какие непустых элементов в результирующем наборе перекрестного соединения. **NonEmptyCrossjoin** функции отношениях **NON_EMPTY_BEHAVIOR** Задание вычисляемых мер.  
  
> [!IMPORTANT]  
>  Эта функция устарела, использовать ее не следует. Она сохранена только для поддержки обратной совместимости. Вместо этого следует использовать [Exists (многомерные Выражения)](../mdx/exists-mdx.md) функцию с аргументом имя группы мер или [NonEmpty (многомерные Выражения)](../mdx/nonempty-mdx.md) функции.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
