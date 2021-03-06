---
title: Изменение определения для политики исправности ресурсов (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.UTILITY.ADMINISTRATION.F1
ms.assetid: 27bec0b6-92e9-448e-8c70-fe36802cf128
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8869d438ce1f6338b1bb994df054cd21783b7354
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135024"
---
# <a name="modify-a-resource-health-policy-definition-sql-server-utility"></a>Изменение определения политики исправности ресурсов (служебная программа SQL Server)
  В этом разделе описано, как изменить определение политики исправности ресурсов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Прежде чем изменять политику использования ресурсов в служебной программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо создать точку управления служебной программой (UCP). Дополнительные сведения см. в разделе [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Для приложений уровня данных и управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно настроить политики использования ресурсов программы. Политика использования ресурсов может быть задана глобально для всех приложений уровня данных и управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо ее можно задать индивидуально для отдельных приложений уровня данных и управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, можно реализовывать глобальные политики и задавать собственные определения политик для отдельных приложений уровня данных или управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="modify-global-resource-utilization-policies-in-a-sql-server-utility"></a>Изменение глобальных политик использования ресурсов в программе SQL Server Utility.  
  
1.  Подключитесь к пункту управления программой в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  На панели навигации обозревателя программ щелкните **Администрирование программ** , чтобы просмотреть или изменить глобальные политики наблюдения, а затем перейдите на вкладку **Политика** панели содержимого.  
  
3.  На панели содержимого обозревателя программ выберите **Задать глобальные политики наблюдения приложений уровня данных** или **Задать глобальные политики для управляемых экземпляров** , щелкнув стрелку или описание политики.  
  
4.  С помощью элементов управления, расположенных справа от описаний политик, задайте пороговые значения политики недостаточного и чрезмерного использования.  
  
5.  При необходимости воспользуйтесь кнопками **Применить**, **Отказаться**или **По умолчанию** . Изменение политики может отразиться на панели мониторинга и в представлении списка программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] лишь через некоторое время, вплоть до 15 минут.  
  
6.  Чтобы обновить данные, на панели навигации обозревателя программ щелкните правой кнопкой мыши узел **Администрирование программы** и выберите команду **Обновить**.  
  
#### <a name="modify-resource-health-policy-definitions-for-an-individual-data-tier-application-or-an-individual-managed-instance-of-sql-server-in-a-sql-server-utility"></a>Измените определения политик исправности ресурсов для отдельного приложения уровня данных или управляемого экземпляра SQL Server в программе SQL Server Utility  
  
1.  Подключитесь к пункту управления программой в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  На панели навигации обозревателя программ щелкните **Развернутые приложения уровня данных**или **Управляемые экземпляры**, чтобы просмотреть или изменить политики наблюдения для отдельных приложений уровня данных или управляемых экземпляров.  
  
3.  В списке на панели содержимого обозревателя программ щелкните имя приложения уровня данных или экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , политики которого нужно изменить, а затем перейдите на вкладку **Данные политики** .  
  
4.  Выберите политику для просмотра или изменения, щелкнув стрелку или описание политики. Глобальные политики выбраны по умолчанию.  
  
5.  Установите переключатель в положение **Переопределять глобальную политику** , чтобы переопределить глобальные политики и реализовать определение отдельной политики для указанного приложения уровня данных.  
  
6.  С помощью элементов управления, расположенных справа от описания политики, задайте пороговые значения политики недостаточного и чрезмерного использования.  
  
7.  При необходимости воспользуйтесь кнопками **Применить**, **Отказаться**или **По умолчанию** . Изменение политики может отразиться на панели мониторинга и в представлении списка программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] лишь через некоторое время, вплоть до 15 минут.  
  
8.  Чтобы обновить данные, на панели навигации обозревателя программ щелкните правой кнопкой мыши узел **Развернутые приложения уровня данных** и выберите команду **Обновить**.  
  
## <a name="see-also"></a>См. также  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Просмотр результатов политики исправности ресурсов (служебная программа SQL Server)](view-resource-health-policy-results-sql-server-utility.md)  
  
  
