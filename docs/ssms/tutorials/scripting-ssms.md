---
Title: 'Tutorial: Script Objects in SQL Server Management Studio'
description: Учебник по созданию скриптов для объектов в SSMS.
keywords: SQL Server, SSMS, SQL Server Management Studio, скрипты, написание скриптов
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: 2ee56bc26c22f91af7bf156ea967c19b61eab881
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="tutorial-script-objects-in-sql-server-management-studio"></a>Учебник: создание скриптов для объектов в среде SQL Server Management Studio
В этом учебнике вы научитесь создавать скрипты Transact-SQL (T-SQL) для различных объектов, доступных в SQL Server Management Studio.  В нем приводятся примеры создания скриптов для следующих объектов: 
 - запросов при выполнении действий в графическом пользовательском интерфейсе;
 - баз данных двумя разными способами ("Сформировать скрипт как" и "Создать скрипт");
 - Таблицы
 - Хранимые процедуры
 - Расширенные события

Если говорить коротко, создать скрипт для любого объекта в **обозревателе объектов** можно, щелкнув его правой кнопкой мыши и выбрав пункт **Создать скрипт для объекта как**. 


## <a name="prerequisites"></a>предварительные требования
Для работы с этим учебником требуется среда SQL Server Management Studio, доступ к SQL Server и база данных AdventureWorks. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Скачайте [образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). 
    - Инструкции по восстановлению баз данных в SSMS можно найти в статье [Восстановление базы данных](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


## <a name="script-queries-from-gui"></a>Создание скриптов для запросов в графическом пользовательском интерфейсе
Каждый раз при выполнении задачи с помощью графического пользовательского интерфейса в SSMS можно также создать код T-SQL, связанный с этой задачей. Ниже приведены примеры выполнения этого действия при создании резервной копии базы данных и сжатии журнала транзакций.  Аналогичные инструкции применимы к любому действию, выполняемому в графическом пользовательском интерфейсе. 

### <a name="scriptt-sql-when-backing-up-a-database"></a>Создание скрипта T-SQL при резервном копировании базы данных
1. Подключитесь к серверу SQL Server.
2. Разверните узел **Базы данных** .
3. Щелкните правой кнопкой мыши имя базы данных и выберите пункты **Задачи** > **Создать резервную копию**.

    ![Резервное копирование базы данных](media/scripting-ssms/backupdb.png)

4. Настройте резервное копирование требуемым образом. В этом учебнике оставлены все параметры по умолчанию. Все изменения, внесенные в этом окне, также отражаются в скрипте. 
5. Выберите команду **Скрипт** > **Создать скрипт действия в новом окне запроса**.
 
    ![Скрипт для резервного копирования базы данных](media/scripting-ssms/scriptdbbackup.PNG)
6. Просмотрите код T-SQL в окне запроса: 

    ![Скрипт для резервного копирования базы данных](media/scripting-ssms/dbbackupscript.PNG)


### <a name="script-t-sql-when-shrinking-the-transaction-log"></a>Создание скрипта T-SQL при сжатии журнала транзакций
1. Щелкните правой кнопкой мыши имя базы данных и выберите пункты **Задачи** > **Сжатие** > **Файлы**.

     ![Сжатие файлов](media/scripting-ssms/shrinkfiles.png)

2. В раскрывающемся списке **Тип файла** выберите **Журнал**.

    ![Сжатие журнала транзакций](media/scripting-ssms/shrinktlog.png)

3. В меню **Скрипт** выберите команду **Записать скрипт в буфер обмена**.

    ![Вывести скрипт в буфер обмена](media/scripting-ssms/scriptactiontoclipboard.png)

4. Откройте окно **Новый запрос** и вставьте текст (щелкните в окне правой кнопкой мыши и выберите команду **Вставить**):

    ![Вставка скрипта](media/scripting-ssms/paste.png)


## <a name="script-databases"></a>Создание скриптов для баз данных
В следующем разделе показано, как создать скрипт для базы данных с помощью команды **Сформировать скрипт как** или **Сформировать скрипты**.  Команда **Сформировать скрипт как** повторно создает базу данных и параметры конфигурации для нее. Команда **Сформировать скрипты** создает скрипты для всех объектов в базе данных, но не для данных. Чтобы включить данные в скрипт, необходимо использовать [мастер импорта и экспорта](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/start-the-sql-server-import-and-export-wizard).  


### <a name="script-database-using-script-option"></a>Создание скрипта для базы данных с помощью команды формирования скрипта
1. Подключитесь к серверу SQL Server.
2. Разверните узел **Базы данных** .
3. Щелкните правой кнопкой мыши базу данных и выберите пункт **Создать скрипт для базы данных**.

    ![Создание скрипта для базы данных](media/scripting-ssms/scriptdb.png)

4. Просмотрите запрос на создание базы данных в окне: 

    ![Скрипт для базы данных](media/scripting-ssms/scriptedoutdb.png)
    - Эта команда включает в скрипт только параметры конфигурации базы данных.  

### <a name="script-database-using-generate-scripts-option"></a>Создание скрипта для базы данных с помощью команды "Сформировать скрипты"
1. Подключитесь к серверу SQL Server.
2. Разверните узел **Базы данных** .
3. Щелкните правой кнопкой мыши имя базы данных и выберите пункты **Задачи** > **Сформировать скрипты**.

    ![Создание скриптов для базы данных](media/scripting-ssms/generatescriptsfordb.png)

4. Нажмите кнопку **Далее**. В следующем окне можно выбрать, следует ли создать скрипт для всей базы данных или для определенных объектов в ней. 
 
    ![Создание скриптов для объектов](media/scripting-ssms/scriptobjects.png)
 
5. Выберите **Далее**. На этом экране можно настроить место сохранения скрипта. 
    - Кроме того, можно настроить дополнительные параметры, нажав кнопку **Дополнительно**.

    ![Дополнительные параметры скрипта](media/scripting-ssms/advancedscripts.png)

6. Когда вы будете готовы продолжить, нажимайте кнопку **Далее**, пока скрипты не будут созданы и не появится экран **завершения**. Скрипт базы данных будет находиться в том месте, где он был сохранен в шаге 5. 
    - В результате этой процедуры создается скрипт для схемы и различных объектов базы данных, но не для данных. 
 
## <a name="script-tables"></a>Создание скриптов для таблиц
В этом разделе описывается, как создать скрипты для таблиц базы данных.

1. Подключитесь к серверу SQL Server.
2. Разверните узел **Базы данных**.
3. Разверните узел базы данных **AdventureWorks**. 
4. Разверните узел **Таблицы**.
5. Щелкните правой кнопкой мыши таблицу, для которой необходимо создать скрипт, и выберите пункт **Создать скрипт для таблицы**.
    - В открывшемся окне можно выполнить различные действия, например создать таблицу или вставить в нее данные. 
    
    ![Таблица скрипта](media/scripting-ssms/scripttable.png)
 
## <a name="script-stored-procedures"></a>Создание скриптов для хранимых процедур
В этом разделе описывается, как создать скрипты для хранимых процедур. 

1. Подключитесь к серверу SQL Server.
2. Разверните узел **Базы данных**.
3. Разверните узел **Программируемость**. 
4. Разверните узел **Хранимые процедуры**.
5. Щелкните правой кнопкой мыши нужную хранимую процедуру и выберите пункт **Создать скрипт для хранимой процедуры**.
    
    ![Создание скриптов для хранимых процедур](media/scripting-ssms/scriptstoredprocedure.PNG)

## <a name="script-extended-events"></a>Создание скриптов для расширенных событий
В этом разделе описывается, как создать скрипты для [расширенных событий](https://docs.microsoft.com/en-us/sql/relational-databases/extended-events/extended-events). 

1. Подключитесь к серверу SQL Server.
2. Разверните узел **Управление**.
3. Разверните узел **Расширенные события**.
4. Разверните узел **Сеансы**.
5. Щелкните правой кнопкой мыши нужный расширенный сеанс и выберите пункт **Создать скрипт для сеанса**.

    ![Создание скриптов для расширенных событий](media/scripting-ssms/scriptxevents.png) 

## <a name="next-steps"></a>Следующие шаги
В следующей статье описываются готовые шаблоны, имеющиеся в SSMS. 

Перейдите к следующей статье, чтобы узнать больше
> [!div class="nextstepaction"]
> [Кнопка дальнейших действий](templates-ssms.md)

