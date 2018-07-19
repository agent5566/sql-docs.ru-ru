---
title: Предоставление разрешений на объект источника данных (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dbe08e5e23b8c40ddeba9efa99c151314d499916
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243724"
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a>Предоставление разрешений объекту источника данных (службы Analysis Services
  Обычно, большинству пользователей службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] нет необходимости в доступе к источникам данных, которые обуславливают проект службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . обычно пользователи лишь запрашивают данные в рамках базы данных службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Однако в контексте интеллектуального анализа данных, например выполнения прогнозов, основанных на модели интеллектуального анализа данных, пользователю необходимо соединить обучающие данные, полученные моделью интеллектуального анализа данных, с данными, предоставленными пользователем. Для подключения источника данных, содержащего предоставленные пользователем данные, пользователь использует запрос расширений интеллектуального анализа данных, в котором содержится либо предложение [OPENQUERY (DMX)](/sql/dmx/source-data-query-openquery), либо предложение [OPENROWSET (DMX)](/sql/dmx/source-data-query-openrowset).  
  
 Чтобы выполнить DMX-запрос, соединяющийся с источником данных, пользователю необходимо обладать доступом к объекту источника данных в рамках базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . По умолчанию, только Администраторы Сервера и Базы данных имеют доступ к объектам источника данных. Это значит, что пользователь не может получить доступ к объекту источника данных до тех пор, пока администратор не предоставит ему разрешения.  
  
> [!IMPORTANT]  
>  Из соображений безопасности выдача DMX-запросов с использованием открытой строки соединения в предложении OPENROWSET отключена.  
  
## <a name="set-read-permissions-to-a-data-source"></a>Настройка Разрешений на чтение источнику данных  
 Роли базы данных может быть отказано в разрешениях на доступ к объекту источника данных, либо предоставлены разрешения на чтение.  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]соединитесь с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], разверните узел **Роли** для соответствующей базы данных в обозревателе объектов, а затем щелкните роль базы данных (или создайте новую).  
  
2.  На вкладке **Доступ к Источнику Данных** , поместите объект источника данных в список **Источник Данных** , а затем выберите **Чтение** в списке **Доступ** для источника данных. Если данный параметр недоступен, проверьте вкладку **Общие** , чтобы проверить, выбран ли Полный Доступ. Если Полный Доступ уже предоставляет разрешение, вы не сможете переопределить разрешения на источнике данных.  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a>Работа со строкой соединения, используемой объектом источника данных  
 Источник данных содержит строку соединения, используемую для подключения к основному источнику данных. В такой строке соединения могут указываться следующие параметры:  
  
-   **Указание имени пользователя и пароля**  
  
     Если в строке соединения, используемой объектом источника данных, указывается имя пользователя и пароль, то может возникнуть необходимость в создании нескольких объектов источника данных, каждому из которых будет предоставлена отдельная учетная запись пользователя. Создание нескольких объектов источника данных позволяет пользователям получать доступ к определенным объектам источника данных и предотвращает доступ таких пользователей к другим объектам источника данных. Указанные другие объекты источника данных могут использоваться самими службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для обработки объектов, например кубов и моделей интеллектуального анализа данных.  
  
-   **Использование проверки подлинности Windows**  
  
     Если в строке соединения, используемой объектом источника данных, указывается проверка подлинности Windows, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] должны иметь возможность выполнить олицетворение клиента. Если источник данных находится на удаленном компьютере, два компьютера должны быть доверенными для олицетворения с использованием проверки подлинности Kerberos, в противном случае запрос обычно завершается ошибкой. Подробнее см. в разделе [Configure Analysis Services for Kerberos constrained delegation](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) .  
  
     Если клиент не разрешает олицетворение (через значение уровня олицетворения в OLE DB и другие компоненты системы), служба [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытается создать анонимное соединение к базовому источнику данных. Анонимные соединения к удаленным источникам данных редко являются успешными, так как большинство источников данных не принимает анонимные соединения).  
  
## <a name="see-also"></a>См. также  
 [Источники данных в многомерных моделях](data-sources-in-multidimensional-models.md)   
 [Свойства строки подключения &#40;служб Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md)   
 [Методики проверки подлинности, поддерживаемые службами Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Предоставление настраиваемого доступа к данным измерения &#40;служб Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Предоставление разрешений кубу или модели &#40;служб Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Предоставление настраиваемого доступа к данным ячейки &#40;служб Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
  