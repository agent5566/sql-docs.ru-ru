---
title: Определение порядка обработки для статей публикации слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: d151e2c5-cf50-4cb3-a829-8f32455dbd66
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 569767e74c6666a68b41b5af9914a5a028522bc1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174054"
---
# <a name="specify-the-processing-order-of-merge-articles"></a>Указание порядка обработки статей публикации слиянием
  Начиная с версии [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], порядок обработки статей для публикаций слиянием, принятый по умолчанию, можно переопределять. Это полезно, например, при определении ссылочной целостности с помощью триггеров и при этом триггеры должны запускаться в конкретном порядке.  
  
 **Указание порядка обработки статей**  
  
-   Программирование репликации на Transact-SQL: [Определение порядка обработки для статей таблиц слияния (программирование репликации на языке Transact-SQL)](../publish/specify-the-processing-order-of-merge-table-articles.md)  
  
## <a name="how-processing-order-is-determined"></a>Как определяется порядок обработки  
 Во время синхронизации слияния статьи по умолчанию обрабатываются в том порядке, который требуют зависимости между объектами, в том числе ограничения декларативной ссылочной целостности (DRI), определенные для базовых таблиц. Обработка включает нумерацию изменений в таблице и применение этих изменений. Если DRI отсутствуют, но для статей таблиц имеются фильтры соединения или логические записи, то статьи обрабатываются в том порядке, который требуют эти фильтры и логические записи. Статьи, не связанные с какой-либо другой статьей через DRI, фильтры соединения, логические записи и другие зависимости обрабатываются в соответствии с псевдонимами в системной таблице [sysmergearticles (Transact-SQL)](/sql/relational-databases/system-tables/sysmergearticles-transact-sql).  
  
 Рассмотрим публикацию, включающую таблицы **SalesOrderHeader** и **SalesOrderDetail** с первичным ключевым столбцом **SalesOrderID** в таблице **SalesOrderHeader** и соответствующим внешним ключевым столбцом **SalesOrderID** в таблице **SalesOrderDetail** . Во время синхронизации репликация слиянием препятствует нарушениям внешнего ключа путем вставки новых строк в столбец **SalesOrderHeader** перед тем, как вставить соответствующие строки в столбец **SalesOrderDetail**. Точно так же строки удаляются из столбца **SalesOrderDetail** перед удалением соответствующих строк из столбца **SalesOrderHeader**.  
  
 Однако в некоторых приложениях ссылочная целостность принудительно навязывается через триггеры базы данных или на уровне приложения, а не через DRI. В приведенной выше публикации таблица **SalesOrderDetail** вместо DRI могла бы иметь триггер Insert, который перед вставкой проверял бы, что в таблице **SalesOrderHeader** существует связанная строка. Таблица**SalesOrderHeader** могла бы иметь триггер Delete, который перед удалением проверял бы, что в таблице **SalesOrderDetail** отсутствует связанная строка. Репликация слиянием перед указанием порядка обработки не учитывает триггеры, потому что она перед запуском триггера не может определить, каков будет его результат. Точно так же репликация не может учитывать ограничения, определенные на уровне приложения.  
  
 Если ссылочная целостность сохраняется с помощью триггеров или на уровне приложения, необходимо задать порядок, в котором будут обрабатываться статьи. В примере с триггерами следовало бы указать, что таблица **SalesOrderHeader** должна обрабатываться раньше **SalesOrderDetail**, потому что упорядочивание статей основано на порядке вставки. Репликация слиянием автоматически меняет этот порядок на обратный для удалений. Репликация слиянием не завершится неудачей, если статьи не упорядочены, потому что, если происходит нарушение ограничения, агент слияния продолжает обрабатывать статьи. Затем, после обработки остальных статей, он пытается выполнить сбойные операции. При указании порядка статей просто исключаются повторные попытки и связанная с ними дополнительная обработка. Если указать неверный порядок (например, если он задает обработку записей с подробными данными до обработки записей заголовков), репликация слиянием будет продолжать обработку до ее успешного завершения.  
  
## <a name="see-also"></a>См. также  
 [Параметры статьи для репликации слиянием](article-options-for-merge-replication.md)   
 [Группирование изменений в связанных строках с помощью логических записей](group-changes-to-related-rows-with-logical-records.md)   
 [Join Filters](join-filters.md)  
  
  
