---
title: "Синтаксический анализ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSE
- PARSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PARSE function
ms.assetid: 6a2dbf10-f692-471b-9458-24d246963049
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b332b92c77340c9cc7f6276d28286e048b2b0f2b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="parse-transact-sql"></a>PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает результат выражения, преобразованный в требуемый тип данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *string_value*  
 **nvarchar**(4000) значение, представляющее форматированное значение для преобразования в указанный тип данных.  
  
 *string_value* должно быть допустимым представлением требуемого типа данных, то инструкция PARSE выдаст ошибку.  
  
 *Тип данных*  
 Литеральное значение, представляющее тип данных, запрошенный в качестве для результата.  
  
 *язык и региональные параметры*  
 Необязательная строка, идентифицирующая культуру, в котором *string_value* форматируется.  
  
 Если *языка и региональных параметров* аргумент не указан, то используется язык текущего сеанса. Язык может быть задан неявно или явно с использованием инструкции SET LANGUAGE. *язык и региональные параметры* принимает любой язык и региональные параметры, поддерживаемые платформой .NET Framework; это не ограничивается языками, поддерживаемыми [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если *языка и региональных параметров* аргумент не является допустимым, инструкция PARSE выдаст ошибку.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает результат выражения, переведенный в требуемый тип данных.  
  
## <a name="remarks"></a>Замечания  
 Значения NULL, передаваемые в качестве аргументов для PARSE, рассматриваются двумя способами:  
  
1.  Если передается константа NULL, возникает ошибка. Значение NULL не может быть преобразовано в другой тип данных с учетом культуры.  
  
2.  При передаче параметра со значением NULL во время выполнения происходит возврат значения NULL во избежание отмены всего пакета.  
  
 Используйте инструкцию PARSE только для преобразования данных из строкового типа в типы даты или времени и числовой тип. Для общих преобразований типов данных продолжайте использовать CAST и CONVERT. Следует учитывать, что разбор строкового значения приводит к некоторой потере производительности.  
  
 Синтаксический анализ зависит от наличия из .NET Framework Common Language Runtime (CLR).  
  
 Данная функция не будет работать удаленно, поскольку возможность ее работы зависит от наличия среды CLR. Удаленный вызов функции, требующей наличия среды CLR, приведет к ошибке на удаленном сервере.  
  
 **Дополнительные сведения о параметре data_type**  
  
 Значения для *data_type* параметра зависят от типов, приведенных в следующей таблице, включая стили. Представленные сведения о стилях позволяют определить, какие типы шаблонов разрешены. Дополнительные сведения о стилях см. в документации платформы .NET Framework для **System.Globalization.NumberStyles** и **параметра DateTimeStyles** перечисления.  
  
|Категория|Тип|Тип .NET Framework|Используемые стили|  
|--------------|----------|-------------------------|-----------------|  
|Числовой|bigint|Int64|NumberStyles.Number|  
|Числовой|int|Int32|NumberStyles.Number|  
|Числовой|smallint|Int16|NumberStyles.Number|  
|Числовой|tinyint|Byte|NumberStyles.Number|  
|Числовой|decimal|Decimal|NumberStyles.Number|  
|Числовой|numeric|Decimal|NumberStyles.Number|  
|Числовой|float|Double|NumberStyles.Float|  
|Числовой|real|Один|NumberStyles.Float|  
|Числовой|smallmoney|Decimal|NumberStyles.Currency|  
|Числовой|money|Decimal|NumberStyles.Currency|  
|Дата и время|date|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|time|TimeSpan|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|datetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|smalldatetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|datetime2|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|datetimeoffset|DateTimeOffset|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
  
 **Дополнительные сведения о параметре культуры**  
  
 В следующей таблице показаны сопоставления между языками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и культурами платформы .NET Framework.  
  
|Полное имя|Псевдоним|LCID|Конкретная культура|  
|---------------|-----------|----------|----------------------|  
|us_english|Английский|1033|ru-RU|  
|Deutsch|Немецкий|1031|de-DE|  
|Français|Французский|1036|fr-FR|  
|日本語|Японский|1041|ja-JP|  
|Dansk|Датский|1030|da-DK|  
|Español|Испанский|3082|es-ES|  
|Italiano|Итальянский|1040|it-IT|  
|Nederlands|Нидерландский|1043|nl-NL|  
|Norsk|Норвежский|2068|nn-NO|  
|Português|Португальский|2070|pt-PT|  
|Suomi|Финский|1035|fi|  
|Svenska|Шведский|1053|sv-SE|  
|čeština|Чешский|1029|Cs-CZ|  
|magyar|Венгерский|1038|Hu-HU|  
|polski|Польский|1045|Pl-PL|  
|română|Румынский|1048|Ro-RO|  
|hrvatski|Хорватский|1050|hr-HR|  
|slovenčina|Словацкий|1051|Sk-SK|  
|slovenski|Словенский|1060|Sl-SI|  
|ελληνικά|Греческий|1032|El-GR|  
|български|Болгарский|1026|bg-BG|  
|русский|Русский|1049|Ru-RU|  
|Türkçe|Турецкий|1055|Tr-TR|  
|British|British English|2057|en-GB|  
|eesti|Эстонский|1061|Et-EE|  
|latviešu|Латышский|1062|lv-LV|  
|lietuvių|Литовский|1063|lt-LT|  
|Português (Brasil)|Бразильский|1046|pt-BR|  
|繁體中文|Китайский (традиционный)|1028|zh-TW|  
|한국어|Корейский|1042|Ko-KR|  
|简体中文|Китайский (упрощенный)|2052|zh-CN|  
|Арабский|Арабский|1025|ar-SA|  
|ไทย|Тайский|1054|Th-TH|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-parse-into-datetime2"></a>A. PARSE в datetime2  
  
```  
SELECT PARSE('Monday, 13 December 2010' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
2010-12-13 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-parse-with-currency-symbol"></a>Б. PARSE с символом денежной единицы  
  
```  
SELECT PARSE('€345,98' AS money USING 'de-DE') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
345.98  
  
(1 row(s) affected)  
```  
  
### <a name="c-parse-with-implicit-setting-of-language"></a>В. PARSE с неявным заданием языка  
  
```  
-- The English language is mapped to en-US specific culture  
SET LANGUAGE 'English';  
SELECT PARSE('12/16/2010' AS datetime2) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
2010-12-16 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
  
