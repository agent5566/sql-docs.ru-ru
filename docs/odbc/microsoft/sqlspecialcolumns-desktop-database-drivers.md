---
title: SQLSpecialColumns (драйверы для настольных систем баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f319e6a28a1eba5f803e9cf7f7087f45f227fd87
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840012"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (драйверы для баз данных на настольном компьютере)
Уникальный индекс будет возвращаться (если он существует) SQL_BEST_ROWID флажка в *fColType*. Результирующий набор не возвращается для флага SQL_ROWVER.  
  
 Все идентификаторы строк имеют область SQL_SCOPE_CURROW.  
  
 Сопоставление шаблонов не поддерживается для либо *szTableQualifier* или *szTableName* аргумент.
