---
title: Метод getXopenStates (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ab68f24cce30a2e0d015daff00b67cd01b6545e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839199"
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Метод getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **логическое** значение, указывающее, включено ли преобразование состояний SQL в состояния, соответствующие стандарту xopen.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если включено преобразование состояний SQL в состояния, соответствующие стандарту xopen. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство xopenStates имеет значение **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] состояний SQL преобразует с xopen. Значение по умолчанию — **false**, что драйвер JDBC для формирования коды состояний SQL 99. Если состояние xopenStates не задано, метод getXopenStates возвращает значение по умолчанию **false**.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
