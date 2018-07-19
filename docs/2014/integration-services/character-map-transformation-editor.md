---
title: Символ Map Transformation Editor | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
caps.latest.revision: 25
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 94857d436adf11eb8cc9732a20918478457d95fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223741"
---
# <a name="character-map-transformation-editor"></a>Редактор преобразования «Таблица соответствия символов»
  Диалоговое окно **Редактор преобразования "Таблица соответствия символов"** используется для выбора строковых функций, применяемых к данным столбцов, и для задания того, будет ли сопоставление приводить к замене на месте или к добавлению нового столбца.  
  
 Дополнительные сведения о преобразовании «Таблица символов» см. в разделе [Character Map Transformation](data-flow/transformations/character-map-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Флажки используются для выбора столбцов, подлежащих преобразованию строковыми функциями. Результаты выбора отобразятся в таблице внизу.  
  
 **Входной столбец**  
 Просмотрите выбранные входные столбцы из вышеприведенной таблицы. Также можно изменить или удалить выбор, используя список доступных входных столбцов.  
  
 **Назначение**  
 Укажите, необходимо ли сохранять результаты строковых операций в том же месте, используя существующий столбец, или сохранять измененные данные в виде нового столбца.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Создать столбец|Сохранить данные в новом столбце. Присвойте столбцу имя в поле **Псевдоним выхода**.|  
|Замена на месте|Сохранить измененные данные в существующем столбце.|  
  
 **Операция**  
 Выберите из списка строковые функции, которые нужно применить к данным столбца.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Нижний регистр|Преобразовать в нижний регистр.|  
|Верхний регистр|Преобразовать в верхний регистр.|  
|Обратный порядок байтов|Преобразовать путем обращения порядка байтов.|  
|Хирагана|Преобразовать японские символы катаканы в хирагану.|  
|Катакана|Преобразовать японские символы хираганы в катакану.|  
|Половинная ширина|Преобразовать полноширинные символы в полуширинные.|  
|Полная ширина|Преобразовать полуширинные символы в полноширинные.|  
|Регистр по правилам языка|Применить лингвистические правила регистра (простое сопоставление регистра Юникода для локали Turkic и других) вместо системных правил.|  
|Китайский (упрощенный)|Преобразовать символы китайского (традиционного) в китайский (упрощенный).|  
|Китайский (традиционный)|Преобразовать символы китайского (упрощенного) в китайский (традиционный).|  
  
 **Псевдоним выхода**  
 Введите псевдоним для каждого выходного столбца. Значением по умолчанию является **Copy of** , за которым следует имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
 **Настройка вывода ошибок**  
 Диалоговое окно [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) для указания параметров обработки ошибок в этом преобразовании.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  