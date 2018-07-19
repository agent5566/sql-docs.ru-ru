---
title: Файлы ярлыков запросов (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8bb8d6f7f3f9864d6b16488eefe409032c66ceee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274760"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a>Файлы ярлыков запросов (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]файл ярлыка запроса позволяет быстро устанавливать соединение и загружать часто используемые данные. Они могут также использоваться в том случае, если необходим обмен данными MDS с другими пользователями. Вместо сохранения и отправки листа по электронной почте можно сохранить файл ярлыка запроса и отправить его. Это гарантирует, что и вы, и ваш адресат будете получать из репозитория MDS самые актуальные данные.  
  
 Файлы ярлыков запросов — это XML-файлы, которые содержат следующие данные.  
  
-   Соединение с репозиторием MDS.  
  
-   Модель, версия и сущность.  
  
-   Все фильтры, применявшиеся при создании ярлыка.  
  
-   Порядок столбцов слева направо, заданный при создании ярлыка.  
  
 Эти файлы можно сохранить в списке и выбрать при открытии надстройки. Их также можно экспортировать на компьютер или в общую папку или отправить другому пользователю.  
  
## <a name="queryopener-application"></a>Приложение QueryOpener  
 Все пользователи, установившие [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , имеют установленное приложение QueryOpener. Оно служит для открытия файлов ярлыков запросов в [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]. Если дважды щелкнуть файл ярлыка запроса, то это приложение автоматически открывает его в надстройке.  
  
 При открытии файла ярлыка запроса в приложении вам будет предложено сделать соединение «безопасным», а это означает, что вы доверяете содержимому из этого источника. Каждый раз, когда соединение помечается как безопасное, оно добавляется в список. Если нужно очистить этот список, откройте диалоговое окно **Настройки** и в разделе **Серверы, добавленные в список безопасных** нажмите кнопку **Очистить все**.  
  
 Расположение по умолчанию для приложения — *диск*: \Program Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.  
  
 Существует два способа, чтобы открыть файлы ярлыков запросов: их можно импортировать или дважды щелкнуть, и он открывается автоматически.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Сохранение содержимого активного листа в виде файла ярлыка запроса.|[Сохранение файла ярлыка запроса (надстройка MDS для Excel)](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Отправка файла ярлыка запроса, который представляет содержимое активного листа.|[Отправка файла ярлыка запроса по электронной почте (надстройка MDS для Excel)](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Соединения (надстройка MDS для ExcelExcel)](connections-mds-add-in-for-excel.md)  
  
-   [Надстройка служб Master Data Services для Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Безопасность (службы Master Data Services)](../security-master-data-services.md)  
  
  