---
title: Создание набора изменений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 53bdd8ed1fcf4c56ca4c38812383e881d46ba460
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753452"
---
# <a name="create-a-changeset-master-data-services"></a>Создание набора изменений (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Набор изменений — это совокупность ожидающих изменений основных данных. Если сущность требует утверждения изменений, необходимо сохранить ожидающие изменения в наборе изменений, а затем отправить его на утверждение администратору.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь разрешение на доступ к функциональной области обозревателя. Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Необходимо иметь по крайней мере доступ на чтение сущности или одного из ее атрибутов.  
  
## <a name="to-create-a-local-changeset"></a>Создание локального набора изменений  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель и версию, а затем щелкните **Обозреватель**.  
  
2.  Щелкните сущность в меню **Сущности** .  
  
3.  В области справа выберите пункт **Наборы изменений** и щелкните **Создать**.  
  
4.  Введите имя набора изменений и нажмите кнопку **Сохранить**.  
  
     Имя набора изменений должно быть уникальным в пределах модели.  
  
## <a name="to-create-a-changeset-for-approval"></a>Создание набора изменений для утверждения  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель и версию, а затем щелкните **Обозреватель**.  
  
2.  Щелкните сущность в меню **Сущности** .  
  
3.  Внесите изменения в сущность и нажмите кнопку**ОК**.  
  
4.  Откроется диалоговое окно**Выбор набора изменений** .  
  
5.  Щелкните **Создать**и введите имя набора изменений, а затем нажмите кнопку **Сохранить**. Имя набора изменений должно быть уникальным в пределах модели.  
  
6.  Чтобы использовать существующий набор изменений, щелкните **Существующий** и выберите набор изменений в списке. Доступны только наборы изменений, которые находятся в состояниях "Открыто" или "Отклонено".  
  
## <a name="next-steps"></a>Next Steps  
 [Применение и обновление набора изменений (Master Data Services)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [Утверждение или отклонение набора изменений (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
