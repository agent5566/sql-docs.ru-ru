---
title: Дополнение строк (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 218b5d1aba71e5905937bd5433f9f1316c473ab8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740612"
---
# <a name="string-padding-ssis"></a>Дополнение строк (службы SSIS)
  Средство оценки выражений не проверяет, содержит ли строка начальные и конечные пробелы, и не приводит строки к одинаковой длине перед их сравнением. Если выражения требуют дополнения строк, можно использовать оператор + для сцепления значений столбцов и пустых строк. Дополнительные сведения см. в разделе [+ (объединение) (выражение SSIS)](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 С другой стороны, если надо удалить лишние пробелы, средство оценки выражений предоставляет функции LTRIM, RTRIM и TRIM, которые удаляют начальные либо конечные пробелы, либо и те и другие. Дополнительные сведения см. в разделах [LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM (выражение служб SSIS)](../../integration-services/expressions/rtrim-ssis-expression.md) и [TRIM (выражение служб SSIS)](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  Функция LEN включает в счет начальные и завершающие пробелы.  
  
## <a name="related-content"></a>См. также  
 Техническая статья [Памятка выражений служб SSIS](http://go.microsoft.com/fwlink/?LinkId=746575)на сайте pragmaticworks.com  
  
  
