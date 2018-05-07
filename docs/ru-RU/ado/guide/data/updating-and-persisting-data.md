---
title: Обновление и сохранение данных | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ADO]
- data updates [ADO]
- ADO, updating data
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04114db2c613464d3c6bc73b58c216ae63fe5c85
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updating-and-persisting-data"></a>Обновление и сохранение данных
Предшествующих главах обсуждались, как использовать ADO для получения данных в источнике данных, как перемещение данных и даже о редактировать данные. Конечно Если целью приложения является предоставление пользователям вносить изменения в данные, будет необходимо понять, как сохранить эти изменения. Можно либо сохранить **записей** изменения в файл с помощью **Сохранить** метода, или можно отправить изменения обратно в источник данных для хранилища с помощью **обновление** или  **UpdateBatch** методы.  
  
 В предыдущих главах, вы изменили данные в несколько строк **записей**. ADO поддерживает две основные понятия, относящиеся к Добавление, удаление и изменение строк данных.  
  
 Первый понятие — что не внесены изменения немедленно **записей**; вместо этого они были сделаны во внутренний *буфера копирования*. Если вы решили, что вам не нужно, чтобы изменения, изменения в буфер копирования будут отменены. Если вы решите сохранить изменения, изменения в буфер копирования будут применены к **записей**.  
  
 Второй понятие — что изменения распространяются либо к источнику данных, сразу после объявления работу над строкой завершения (т. е *немедленно* режим), или все изменения в набор строк, собранные до объявления рабочего набора Полный (то есть *пакета* режиме). **LockType** свойство определяет, когда внесения изменений в источнике данных. **adLockOptimistic** или **adLockPessimistic** указывает режима интерпретации пока **adLockBatchOptimistic** пакетный режим. **CursorLocation** свойство может повлиять на который **LockType** доступны параметры. Например **adLockPessimistic** параметр не поддерживается, если **CursorLocation** свойству **adUseClient**.  
  
 В режиме интерпретации, каждый вызов **обновление** метод распространяет изменения в источнике данных. В пакетном режиме, каждый вызов **обновление** или перемещение текущей позиции строки сохраняет изменения в буфер копирования, но только **UpdateBatch** метод распространяет изменения в источнике данных.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление данных](../../../ado/guide/data/updating-data.md)  
  
-   [Сохранение данных](../../../ado/guide/data/persisting-data.md)