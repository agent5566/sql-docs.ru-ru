---
title: "Глобальные параметры (протоколирование) (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12dbcd77-2b90-4fa1-9cf9-239231ea5773
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: df359be112e86522d35e27d8cf49a4515d8745d6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="global-settings-logging-oracletosql"></a>Глобальные параметры (протоколирование) (OracleToSQL)
Используйте **глобальные параметры** диалоговое окно «», чтобы указать параметры ведения журнала для SSMA. Как правило нужно изменить эти параметры только при работе с технической поддержки.  
  
Чтобы открыть это диалоговое окно на **средства** последовательно выберите пункты **глобальные параметры** и нажмите кнопку **ведение журнала** , расположенную в нижней части левой панели.  
  
## <a name="options"></a>Параметры  
**Уровень сообщений**  
Следующие параметры доступны в разделе **уровень сообщений**:  
  
|Параметр|Description|  
|----------|---------------|  
|**[все категории]**|Используется для задания уровня ведения журнала для всех следующих параметров.|  
|**Сборщик**|Метаданные о схеме источника собирает и сохраняет его в проект.|  
|**Преобразователь**|Преобразует структуры объектов базы данных источника, таких как таблицы и хранимые процедуры в соответствующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] структуры.|  
|**Migrator данных**|Миграция данных из базы данных-источника в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**Модуль форматирования**|Подкомпонента преобразователя, который формирует скрипты для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схемы.|  
|**Графический пользовательский интерфейс**|Сообщений, которые появляются при использовании средства SSMA.|  
|**Компоновщик**|Разрешает идентификаторов SQL и предоставляет сведения для других компонентов.|  
|**Другое**|Все сообщения, не входящие в другие категории.|  
|**Средство синтаксического анализа**|Выполняет синтаксический анализ в исходной схеме.|  
|**Синхронизатор**|Загружает источник объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**TreeConverter**|Преобразует объекты в исходных метаданных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных.|  
|**Тест-инженер**|Сообщений, которые появляются при использовании инженер-испытатель SSMA.|  
  
Для каждого параметра в разделе **уровень сообщений**, настройте один из следующих уровней ведения журнала для SSMA:  
  
|||  
|-|-|  
|**Неустранимая ошибка**|Запись в журнал сообщения о неустранимых ошибках.|  
|**Ошибка**|Запись в журнал ошибок и сообщения о неустранимых ошибках.|  
|**Предупреждение**|Запись в журнал предупреждение, ошибки и сообщения о неустранимых ошибках.|  
|**Сведения о**|Запись в журнал информационные, предупреждения, ошибки и сообщения о неустранимых ошибках.|  
|**Отладка**|Запись всех сообщений, включая сообщения в журнал отладки.|  
  
**Путь к файлу журнала**  
Путь к файлу и имя файла журнала SSMA. Чтобы указать другое имя, щелкните по текущему пути и нажмите кнопку обзора (**...** ) кнопки.  
  
**Размер файла журнала**  
Максимальный размер файла журнала в КБ. Минимальный размер — 10 КБ. Размер по умолчанию — 10 240 КБ.  
  
**Общее количество файлов журнала**  
Когда один журнал заполняется, SSMA переименовать файл журнала и начать новый. Используя этот параметр, укажите максимальное количество сохраняемых файлов журнала. Минимальное значение — 2.  
  
