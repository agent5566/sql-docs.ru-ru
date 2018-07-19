---
title: Межбазовые транзакции не поддерживаются для зеркального отображения базы данных или AlwaysOn группы доступности (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6014fcc072e9ce6d85fffc62d76f5ba51f341556
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271710"
---
# <a name="cross-database-transactions-not-supported-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a>Транзакции между базами данных не поддерживаются при зеркальном отображении баз данных или в группах доступности AlwaysOn (SQL Server)
  Транзакции между базами данных и распределенные транзакции не поддерживаются ни [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], ни зеркальным отображением баз данных. вследствие того, что атомарность/целостность транзакции не может быть гарантирована по следующим причинам.  
  
-   Для транзакций между базами данных: каждая база данных фиксирует независимо друг от друга. Поэтому даже в случае с базами данных в одной группе доступности, отработка отказа может произойти после того как одна база данных применит транзакцию, а в другой базе данных она еще не была применена. В случае с зеркальным отображением баз данных этот вопрос вызывает сложности, поскольку при отработке отказа отображаемая база данных обычно находится на другом экземпляре сервера, и даже если обе базы данных зеркально отображаются между двумя одинаковыми партнерами, нет гарантии, что обе базы данных будут переключены на резервный ресурс в одно и то же время.  
  
-   Для распределенных транзакций: после отработки отказа, основной сервер/основная реплика не сможет подключиться к координатору распределенных транзакций на предыдущей основной сервер/основная реплика. Поэтому новый основной сервер/основная реплика не сможет получить состояние транзакции.  
  
 В следующем примере зеркального отображения базы данных показано, как возникает логическое несоответствие. В этом примере приложение использует межбазовую транзакцию для вставки двух строк данных: одна строка вставляется в таблицу зеркально отображаемой базы данных A, другая — в таблицу второй базы данных, B. База данных A зеркально отображается в режиме высокого уровня безопасности с автоматической отработкой отказа. При фиксации транзакции база данных A становится недоступной, и сеанс зеркального отображения автоматически переходит на зеркальное отображение базы данных A.  
  
 После автоматической отработки отказа межбазовая транзакция может успешно зафиксироваться в базе данных B, но не в базе данных, с которой выполнен автоматический переход. Это случится, если исходный основной сервер для базы данных А перед переходом не отправил журнал межбазовых транзакций на зеркальный сервер. После автоматической отработки отказа эта транзакция не будет существовать на новом основном сервере. Базы данных A и B станут несогласованными, поскольку вставленные данные в базе данных B останутся нетронутыми, в то время как вставленные данные в базе данных A будут потеряны.  
  
 Похожее может произойти при использовании транзакций MS DTC. Например, после автоматической отработки отказа новая основная база данных обращается к MS DTC. Но MS DTC не знает о новом основном сервере и завершает все транзакции, готовящиеся к фиксации, которые считаются зафиксированными в других базах данных.  
  
> [!IMPORTANT]  
>  Использование зеркального отображения базы данных или групп доступности вместе с DTC не приводит к неподдерживаемой установке SQL Server. Однако, если база данных является частью сеанса зеркального отображения базы данных или группы доступности и в базе данных также используется DTC, проблемы поддержки будут исследованы Microsoft только в случае, если они не имеют отношения к совместному использованию зеркального отображения базы данных или групп доступности вместе с DTC.  
  
  