---
title: Передача аргументов метода веб-службы | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 92cbee94cad189a4752a2fb3300894dcb1c4c5c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074004"
---
# <a name="supplying-web-service-method-arguments"></a>Передача аргументов методу веб-службы
  Метод веб-службы сервера отчетов отправляет запрос в службу по заданному URL-адресу с помощью протокола SOAP по протоколу HTTP. Служба получает запрос, обрабатывает его, а затем возвращает ответное сообщение. Такие запросы и ответы на них имеют форму XML-документов.  
  
## <a name="optional-parameters"></a>Необязательные параметры  
 В некоторых случаях метод веб-службы может иметь необязательные входные параметры. Даже если входной параметр метода веб-службы является необязательным, его все равно нужно указать и установить для него значение `null` (`Nothing` в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Если для параметра задать значение `null`, то элемент для этого параметра в SOAP-запросе также будет иметь значение `null`.  
  
 В следующем примере используется метод <xref:ReportService2010.ReportingService2010.CreateFolder%2A>, чтобы создать новую папку с именем Product Sales в папке Sales. Если для свойств папки задать значение `null`, то для папки не передаются пользовательские свойства:  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Сложные типы данных  
 Основным классом веб-службы сервера отчетов является <xref:ReportService2010.ReportingService2010>, который используется для вызова операций SOAP или веб-методов класса-посредника. Чтобы обеспечить поддержку этого класса и его методов, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включают определяемые пользователем сложные типы данных, относящиеся к входным и выходным параметрам методов веб-службы. Эти сложные типы данных являются частью создаваемого прокси-класса, который используется при разработке в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Во время создания класса-посредника сложные типы данных, определенные в WSDL-файле, представляются классами-посредниками, которые включают свойства, соответствующие различным элементам SOAP в сложных типах данных. Последовательности таких типов данных становятся массивами объектов, которые можно перечислять в коде. Это устраняет необходимость непосредственной работы с XML-структурами, отправляемыми в сообщениях SOAP. Платформа [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] выполняет необходимые преобразования.  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md)  
  
  
