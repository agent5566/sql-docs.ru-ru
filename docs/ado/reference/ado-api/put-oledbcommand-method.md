---
title: "Метод put_OLEDBCommand | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- put_OLEDBCommand method [ADO]
ms.assetid: ca6a5804-bf5c-4afc-99db-22904bc0b33d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bacb428831a27a0c62c9a92116a6cef54ddd709c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="putoledbcommand-method"></a>Метод put_OLEDBCommand
Этот метод не выполняет никаких действий и всегда возвращает значение S_OK.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT put_OLEDBCommand(  
      IUnknown *pOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *pOLEDBCommand*  
 [in] Указатель на объект команды OLE DB.  
  
## <a name="applies-to"></a>Объект применения  
 [IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)