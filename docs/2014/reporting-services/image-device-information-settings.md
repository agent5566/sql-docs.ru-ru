---
title: Настройки сведений об устройстве вывода изображений | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6737a32eb7597f8115a7ee6797bcf1aedbd006b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220784"
---
# <a name="image-device-information-settings"></a>Настройки сведений об устройстве вывода изображений
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате изображений.  
  
|Настройка|Значение|  
|-------------|-----------|  
|**Столбцы**|Задаваемое число столбцов в отчете. Это значение переопределяет исходные параметры отчета.|  
|**ColumnSpacing**|Интервал между столбцами, который должен быть задан для отчета. Это значение переопределяет исходные параметры отчета.|  
|`DpiX`|Горизонтальное разрешение изображения вывода. Значение по умолчанию — **96**. Применяется к `BMP`, `GIF`, `PNG`, и `TIFF` форматы выходных данных.|  
|`DpiY`|Вертикальное разрешение изображения вывода. Значение по умолчанию — **96**. Применяется к `BMP`, `GIF`, `PNG`, и `TIFF` форматы выходных данных.|  
|**EndPage**|Последняя подготавливаемая к просмотру страница отчета. Значением по умолчанию является значение для `StartPage`.|  
|**MarginBottom**|Задаваемая ширина нижнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, а затем «in» (например, `1in`). Это значение переопределяет исходные параметры отчета.|  
|**MarginLeft**|Задаваемая ширина левого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, а затем «in» (например, `1in`). Это значение переопределяет исходные параметры отчета.|  
|**MarginRight**|Задаваемая ширина правого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, а затем «in» (например, `1in`). Это значение переопределяет исходные параметры отчета.|  
|**MarginTop**|Задаваемая ширина верхнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, а затем «in» (например, `1in`). Это значение переопределяет исходные параметры отчета.|  
|**OutputFormat**|Один из [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) поддерживаемые форматы выходных данных: `BMP`, `EMF`, `GIF`, `JPEG`, `PNG`, или `TIFF`.|  
|**PageHeight**|Задаваемая высота страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, а затем «in» (например, `11in`). Это значение переопределяет исходные параметры отчета.|  
|**PageWidth**|Задаваемая ширина страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, а затем «in» (например, `8.5in`). Это значение переопределяет исходные параметры отчета.|  
|**PrintDpiX**|Горизонтальное разрешение изображения вывода. Значение по умолчанию — `300`. Применяется к расширенного метафайла (`EMF`) формат выходных данных.|  
|**PrintDpiY**|Вертикальное разрешение изображения вывода. Значение по умолчанию — `300`. Применяется к расширенного метафайла (`EMF`) формат выходных данных.|  
|`StartPage`|Первая подготавливаемая к просмотру страница отчета. Значение `0` указывает, что к просмотру подготовлены все страницы. Значение по умолчанию — `1`.|  
  
## <a name="see-also"></a>См. также  
 [Передача настроек сведений об устройстве для модулей подготовки отчетов](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
