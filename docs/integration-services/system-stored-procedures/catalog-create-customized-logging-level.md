---
title: catalog.create_customized_logging_level  | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 20b3ba0a-126f-49bf-b70f-61b2a0fcb750
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aae4a61ed74777c39638d837f9fb1512df24108e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727672"
---
# <a name="catalogcreatecustomizedlogginglevel"></a>catalog.create_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Создает новый настроенный уровень ведения журнала. Дополнительные сведения о настроенных уровнях ведения журналов см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_customized_logging_level [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
    , [ @profile_value = ] profile_value  
    , [ @event_value = ] event_value  
    , [ @level_id = ] level_id OUT   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @level_name = ] *level_name*  
 Название нового существующего настроенного уровня ведения журнала.  
  
 Параметр *level_name* имеет тип **nvarchar(128)**.  
  
 [ @level_description = ] *level_description*  
 Описание нового существующего настроенного уровня ведения журнала.  
  
 Параметр *level_description* имеет тип **nvarchar(1024)**.  
  
 [ @profile_value = ] *profile_value*  
 Статистические данные, которые будут включаться в новый настроенный уровень ведения журнала.  
  
 К допустимым значениям статистических данных относятся следующие. Эти значения соответствуют значениям на вкладке **Статистика** диалогового окна **Управление настроенным уровнем ведения журнала**.  
  
-   Execution = 0  
  
-   Volume = 1  
  
-   Performance = 2  
  
 Параметр *profile_value* имеет тип **bigint**.  
  
 [ @event_value = ] *event_value*  
 События, которые будут включаться в новый настроенный уровень ведения журнала.  
  
 К допустимым значениям событий относятся следующие. Эти значения соответствуют значениям на вкладке **События** диалогового окна **Управление настроенным уровнем ведения журнала**.  
  
|События без контекста событий|События с контекстом событий|  
|----------------------------------|-------------------------------|  
|OnVariableValueChanged = 0<br /><br /> OnExecutionStatusChanged = 1<br /><br /> OnPreExecute = 2<br /><br /> OnPostExecute = 3<br /><br /> OnPreValidate = 4<br /><br /> OnPostValidate = 5<br /><br /> OnWarning = 6<br /><br /> OnInformation = 7<br /><br /> OnError = 8<br /><br /> OnTaskFailed = 9<br /><br /> OnProgress = 10<br /><br /> OnQueryCancel = 11<br /><br /> OnBreakpointHit = 12<br /><br /> OnCustomEvent = 13<br /><br /> Diagnostic = 14<br /><br /> DiagnosticEx = 15<br /><br /> NonDiagnostic = 16|OnVariableValueChanged_IncludeContext = 32<br /><br /> OnExecutionStatusChanged_IncludeContext = 33<br /><br /> OnPreExecute_IncludeContext = 34<br /><br /> OnPostExecute_IncludeContext = 35<br /><br /> OnPreValidate_IncludeContext = 36<br /><br /> OnPostValidate_IncludeContext = 37<br /><br /> OnWarning_IncludeContext = 38<br /><br /> OnInformation_IncludeContext = 39<br /><br /> OnError_IncludeContext = 40<br /><br /> OnTaskFailed_IncludeContext = 41<br /><br /> OnProgress_IncludeContext = 42<br /><br /> OnQueryCancel_IncludeContext= 43<br /><br /> OnBreakpointHit_IncludeContext = 44<br /><br /> OnCustomEvent_IncludeContext = 45<br /><br /> Diagnostic_IncludeContext = 46<br /><br /> DiagnosticEx_IncludeContext = 47<br /><br /> NonDiagnostic_IncludeContext = 48|  
  
 Параметр *event_value* имеет тип **bigint**.  
  
 [ @level_id = ] *level_id* OUT  
 Идентификатор нового настроенного уровня ведения журнала.  
  
 Параметр *level_id* имеет тип **bigint**.  
  
## <a name="remarks"></a>Remarks  
 Чтобы объединить несколько значений в Transact-SQL для аргумента *profile_value* или *event_value*, воспользуйтесь следующим примером. Чтобы захватить события OnError (8) и DiagnosticEx (15), необходимо использовать следующую формулу для расчета *event_value*: `2^8 + 2^15 = 33024`.  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   У пользователя отсутствуют необходимые разрешения.  
  
  
