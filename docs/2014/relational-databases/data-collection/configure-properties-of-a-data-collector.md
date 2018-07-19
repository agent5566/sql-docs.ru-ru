---
title: Настройка свойств сборщика данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce9a591b6e3e347311c7f056b35e7e1353f031d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203459"
---
# <a name="configure-properties-of-a-data-collector"></a>Настройка свойств сборщика данных
  В этом разделе рассматривается настройка свойств сборщика данных.  
  
## <a name="data-collection-properties-general-tab"></a>Свойства сбора данных (вкладка «Общие»)  
 Эта страница используется для настройки параметров хранилища данных управления и указания места хранения собранных данных перед передачей в хранилище данных.  
  
 **Включить сбор данных**  
 Выберите, чтобы включить сбор данных. Результат этого действия такой же, как при запуске хранимой процедуры sp_syscollector_enable_collector. При снятии флажка сбор данных отключается, результат такой же, как при запуске хранимой процедуры sp_syscollector_disable_collector.  
  
 **Server**  
 Отображает имя сервера, на котором будет размещено хранилище данных управления.  
  
 **Имя базы данных**  
 Отображает имя реляционной базы данных, которая используется для хранилища управляющих данных.  
  
 **Проверка соединения**  
 Проверяет соединение с указанным **Сервером** с использованием данных, предоставленных при настройке сборщика данных.  
  
 **Каталог кэша**  
 Указывает каталог, в котором хранятся собранные данные на локальном компьютере до их передачи в хранилище управляющих данных. Если **Каталог кэша** не указан, сборщик данных предпринимает попытку обнаружить переменные среды %TEMP% и %TMP% и использует одно из этих мест в качестве временного хранилища по умолчанию. Если эти переменные среды не заданы, выдается ошибка и запрос для создания каталога кэша.  
  
## <a name="data-collection-properties-advanced-tab"></a>Свойства сбора данных (вкладка «Дополнительно»)  
 Эта страница используется для настройки параметров повторных попыток соединения с хранилищем данных управления.  
  
 **Количество повторных попыток в случае ошибки передачи**  
 Указывает число повторных попыток передачи в хранилище управляющих данных, если передача завершается ошибкой. Значение по умолчанию равно 1.  
  
## <a name="see-also"></a>См. также  
 [Управление сбором данных](data-collection.md)   
 [Настройка хранилища данных управления (среда SQL Server Management Studio)](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  