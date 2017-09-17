---
title: "Числовые функции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], numeric functions
- numeric functions [ODBC]
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f41ae1e8ad665da3db472941ee47afebefa63dd3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="numeric-functions"></a>Числовые функции
В следующей таблице описаны числовые функции, включенные в набор скалярные функции ODBC. Путем вызова **SQLGetInfo** с *типу информации* из SQL_NUMERIC_FUNCTIONS, приложение может определить числовые функции, которые поддерживаются драйвером.  
  
 Все числовые функции возвращают значения типа данных SQL_FLOAT за исключением ABS, ROUND, TRUNCATE, знак, FLOOR и CEILING, которые возвращают значения тех же данных введите в качестве входных параметров.  
  
 Аргументы обозначается как *числовое_выражение* может быть имя столбца, а результат другой скалярной функцией, или *litera цифровой*l, где базовый тип данных может быть представлено как SQL_NUMERIC SQL_ Десятичное число, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL или SQL_DOUBLE.  
  
 Аргументы обозначается как *float_exp* может быть имя столбца, а результат другой скалярной функцией, или *числовой литерал*, где базовый тип данных может быть представлено как SQL_FLOAT.  
  
 Аргументы обозначается как *целое_выражение* может быть имя столбца, а результат другой скалярной функцией, или *числовой литерал*, где базовый тип данных может быть представлено как SQL_TINYINT SQL_ SMALLINT, SQL_INTEGER или sql_bigint не поддерживается.  
  
 Скалярные функции CURRENT_DATE, CURRENT_TIME и CURRENT_TIMESTAMP были добавлены в ODBC версии 3.0 в соответствии со стандартом SQL-92.  
  
|Функция|Description|  
|--------------|-----------------|  
|**ABS (** *числовое_выражение* **)** (ODBC 1.0)|Возвращает абсолютное значение *числовое_выражение*.|  
|**ACOS (** *float_exp* **)** (ODBC 1.0)|Возвращает арккосинус числа *float_exp* как угол, выраженный в радианах.|  
|**ASIN (** *float_exp* **)** (ODBC 1.0)|Возвращает арксинус числа *float_exp* как угол, выраженный в радианах.|  
|**ATAN (** *float_exp* **)** (ODBC 1.0)|Возвращает арктангенс *float_exp* как угол, выраженный в радианах.|  
|**ATAN2 (** *float_exp1*, *float_exp2***)** (ODBC 2.0)|Возвращает арктангенс *x* и *y* координат, указанное *float_exp1* и *float_exp2*соответственно углом выраженный в радианах.|  
|**Верхний ПРЕДЕЛ (** *числовое_выражение* **)** (ODBC 1.0)|Возвращает наименьшее целое число, больше или равно *числовое_выражение*. Возвращаемое значение имеет тот же тип данных в качестве входного параметра.|  
|**COS (** *float_exp* **)** (ODBC 1.0)|Возвращает косинус *float_exp*, где *float_exp* угла в радианах.|  
|**COT (** *float_exp* **)** (ODBC 1.0)|Возвращает котангенс *float_exp*, где *float_exp* угла в радианах.|  
|**ГРАДУСОВ (** *числовое_выражение* **)** (ODBC 2.0)|Возвращает число градусов, преобразованные из *числовое_выражение* радиан.|  
|**EXP (** *float_exp* **)** (ODBC 1.0)|Возвращает значение экспоненты *float_exp*.|  
|**Функция FLOOR (** *числовое_выражение* **)** (ODBC 1.0)|Возвращает наибольшее целое число, меньшее или равное *числовое_выражение*. Возвращаемое значение имеет тот же тип данных в качестве входного параметра.|  
|**ЖУРНАЛ (** *float_exp* **)** (ODBC 1.0)|Возвращает натуральный логарифм числа *float_exp*.|  
|**LOG10 (** *float_exp* **)** (ODBC 2.0)|Возвращает десятичный логарифм *float_exp*.|  
|**MOD (** *integer_exp1*, *integer_exp2***)** (ODBC 1.0)|Возвращает остаток от деления из *integer_exp1* деленная *integer_exp2*.|  
|**PI ()** (ODBC 1.0)|Возвращает значение константы pi как значение с плавающей запятой.|  
|**POWER (** *числовое_выражение*, *целое_выражение***)** (ODBC 2.0)|Возвращает значение *числовое_выражение* в степень *целое_выражение*.|  
|**РАДИАН (** *числовое_выражение* **)** (ODBC 2.0)|Возвращает количество радиан, преобразованные из *числовое_выражение* градусов.|  
|**Функция RAND (**[*целое_выражение*]**)** (ODBC 1.0)|Возвращает случайное значение с плавающей запятой, используя *целое_выражение* как необязательный начального значения.|  
|**ROUND (** *числовое_выражение*, *целое_выражение***)** (ODBC 2.0)|Возвращает *числовое_выражение* округляется до *целое_выражение* помещает справа от десятичной запятой. Если *целое_выражение* отрицательное, *числовое_выражение* округляется до &#124;* целое_выражение*&#124; разрядов слева от десятичной запятой.|  
|**ЗНАК (** *числовое_выражение* **)** (ODBC 1.0)|Возвращает индикатор знак *числовое_выражение*. Если *числовое_выражение* – меньше 1, равно нулю, возвращается. Если *числовое_выражение* равно нулю, то возвращается значение 0. Если *числовое_выражение* больше нуля, возвращается 1.|  
|**SIN (** *float_exp* **)** (ODBC 1.0)|Возвращает синус *float_exp*, где *float_exp* угла в радианах.|  
|**SQRT (** *float_exp* **)** (ODBC 1.0)|Возвращает квадратный корень из *float_exp*.|  
|**TAN (** *float_exp* **)** (ODBC 1.0)|Возвращает тангенс *float_exp*, где *float_exp* угла в радианах.|  
|**TRUNCATE (** *числовое_выражение*, *целое_выражение***)** (ODBC 2.0)|Возвращает *числовое_выражение* усекается до *целое_выражение* помещает справа от десятичной запятой. Если *целое_выражение* отрицательное, *числовое_выражение* усекается до &#124;* целое_выражение*&#124; разрядов слева от десятичной запятой.|