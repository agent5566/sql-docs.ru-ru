---
title: Развертывание пользовательского элемента отчета | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 48e55cfb3eb754af540ca4eb4d19ae415d396f60
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175874"
---
# <a name="how-to-deploy-a-custom-report-item"></a>Развертывание пользовательского элемента отчета
  Чтобы развернуть пользовательский элемент отчета в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], нужно изменить файлы конфигурации сервера отчетов и скопировать сборки времени разработки и времени выполнения в соответствующие папки приложений для конструктора отчетов и сервера отчетов.  
  
### <a name="to-deploy-a-custom-report-item"></a>Развертывание пользовательского элемента отчета  
  
1.  Произведите редактирование файла Rsreportdesigner.config, настроив компоненты времени разработки и компоненты времени выполнения, принадлежащие пользовательскому элементу отчета, для использования в конструкторе.  Следует заметить, что запись `ReportItemName` должна соответствовать атрибуту `CustomReportItemAttribute`, используемому в классе `CustomReportItemDesigner`. Пример:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Произведите редактирование файла Rsreportdesigner.config, зарегистрировав компонент времени выполнения пользовательского элемента отчета. Пример:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Отредактируйте файл Rsssrvpolicy.config, добавив запись `CodeGroup`, предоставляющую соответствующие разрешения для пользовательского элемента отчета. Пример:  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  Скопируйте динамическую библиотеку компонента времени выполнения пользовательского элемента отчета в каталоги %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies и \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin.  
  
5.  Скопируйте динамическую библиотеку компонента времени разработки пользовательского элемента отчета в каталог %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
## <a name="see-also"></a>См. также  
 [Файлы конфигурации служб Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Библиотеки классов пользовательских элементов отчета](custom-report-item-class-libraries.md)  
  
  
