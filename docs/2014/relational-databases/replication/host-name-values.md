---
title: Значения функции HOST_NAME Values | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f116033e54e33bc63893865bdc4339399dde4f4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100762"
---
# <a name="hostname-values"></a>Значения функции HOST_NAME
  Публикации слиянием с параметризованными фильтрами используют функции SUSER_SNAME() или HOST_NAME() для фильтрации данных. Функция задается в мастере создания публикаций или диалоговом окне **Свойства публикации** .  
  
 По умолчанию функция HOST_NAME() возвращает имя компьютера, подключающегося к издателю. При использовании параметризованных фильтров принято заменять это значение, указав новое значение на данной странице мастера. В этом случае функция HOST_NAME() будет возвращать указанное значение вместо имени компьютера. Дополнительные сведения см. в главе "Переопределение значения функции HOST_NAME()" в статье [Параметризованные фильтры строк](merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Если переопределить функцию HOST_NAME(), все вызовы этой функции будут возвращать указанное значение. Убедитесь, что другие приложения не зависят от того, возвращает ли функция HOST_NAME() имя компьютера.  
  
## <a name="options"></a>Параметры  
 **Свойства подписки**  
 Введите значения для каждого подписчика в столбце **Значение HOST_NAME** или оставьте значение по умолчанию, которое соответствует имени компьютера подписчика.  
  
## <a name="see-also"></a>См. также  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Просмотр и изменение свойств подписки по запросу](view-and-modify-pull-subscription-properties.md)   
 [Просмотр и изменение свойств принудительной подписки](view-and-modify-push-subscription-properties.md)   
 [HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql)   
 [Подписка на публикации](subscribe-to-publications.md)  
  
  
