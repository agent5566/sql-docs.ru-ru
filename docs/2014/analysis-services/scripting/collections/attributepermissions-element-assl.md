---
title: Элемент AttributePermissions (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributePermissions
helpviewer_keywords:
- AttributePermissions element
ms.assetid: ac703177-5936-440e-b1a5-a254a89258bc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 00abbc7be0b8efa045074773ee6e2a3526192694
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227964"
---
# <a name="attributepermissions-element-assl"></a>Элемент AttributePermissions (ASSL)
  Содержит коллекцию разрешений атрибутов для отдельного [роли](../objects/role-element-assl.md) элемент с указанным измерением из [куба](../objects/cube-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimensionPermission> <!-- or DimensionPermission -->  
   <AttributePermissions>  
      <AttributePermission>...</AttributePermission>  
      </AttributePermissions>  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubeDimensionPermission](../data-type/permission-data-type-assl.md), [DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
|Дочерние элементы|[AttributePermission](../objects/attributepermission-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Для элемента `DimensionPermission` эта коллекция может содержать только один элемент `AttributePermission` для каждого атрибута.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AttributePermissionCollection>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
