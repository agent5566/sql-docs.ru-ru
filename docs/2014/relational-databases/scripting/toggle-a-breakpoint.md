---
title: Переключение точки останова | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a04f258a7f92c38f560eb0ecc68e7a24e37597a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315614"
---
# <a name="toggle-a-breakpoint"></a>Переключение точки останова
  Установка точки останова для инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] называется переключением точки останова.  
  
## <a name="breakpoints"></a>Точки останова  
 Установленная точка останова отображается значком на серой полосе слева от инструкции. Этот значок называется глифом точки останова. [!INCLUDE[tsql](../../includes/tsql-md.md)] применяются к полной инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Когда точка останова включена, отладчик подсвечивает связанную инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 При наличии в строке нескольких инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] можно включить точку останова для каждой из них. При щелчке серой полосы в левой части окна переключается точка останова для первой инструкции в строке. Чтобы переключить точку останова следующей инструкции, выделите любую часть этой инструкции или переместите курсор в нее и нажмите клавишу F9 либо выберите команду **Переключить точку останова** в меню **Отладка** . Нескольким точкам останова в одной строке соответствует одна глифом точки останова.  
  
 После переключения точки останова можно выполнять различные действия с точкой останова, например изменить свойства или временно отключить. Дополнительные сведения см. в разделе [Точки останова Transact-SQL](transact-sql-breakpoints.md).  
  
## <a name="toggle-a-breakpoint"></a>Переключение точки останова  
 **Переключение точки останова на инструкции языка Transact-SQL**  
  
1.  Щелкните серую полосу слева от инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
2.  Выделите любую часть инструкции или переместите курсор в инструкцию и выполните любое из следующих действий.  
  
    -   Нажмите клавишу F9.  
  
    -   В меню **Отладка** выбрать пункт **Переключить точку останова**.  
  
  