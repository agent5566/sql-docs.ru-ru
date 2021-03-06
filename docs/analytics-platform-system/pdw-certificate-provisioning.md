---
title: Подготовка сертификата PDW - система платформы аналитики | Документы Microsoft
description: Подготовка сертификата PDW страницы аналитика платформы System Configuration Manager импортирует или удаляет сертификат, используемый регион PDW.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ea52c615f4629b579f5f239513c84d851de9e487
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544936"
---
# <a name="pdw-certificate-provisioning---analytics-platform-system"></a>Подготовка сертификата PDW - система платформы аналитики
**Подготовка сертификата PDW** страница Analytics Platform System **Configuration Manager** импортирует или удаляет сертификат, используемый регион PDW. Использование, сертификат для шифрования соединения может помочь безопасного обмена данными с узла управления через клиенты SQL Server, средства, использующие драйверы SQL Server PDW [консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md), и загружает служб Integration Services.  
  
## <a name="prerequisites"></a>предварительные требования  
Прежде чем устанавливать сертификат, выполните следующее:  
  
1.  Получите сертификат безопасности. Если требуются дополнительные сведения о том, как получить сертификат безопасности, обратитесь в службу поддержки Майкрософт.  
  
2.  Сохраните файл сертификата на узел элемента управления в PFX-файл защищен паролем.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>По соображениям безопасности получить доверенный сертификат  
SQL Server PDW поддерживает использование сертификата для шифрования подключения к узлу; включая подключений к **консоли администрирования**.  
  
По умолчанию **консоли администрирования** включает самозаверяющий сертификат, который обеспечивает конфиденциальность, но не проверки подлинности сервера. Это может стать уязвимым для атаки в середине связи. Когда пользователь подключается к консоли администрирования с помощью самозаверяющего сертификата, Internet Explorer возвращает ошибку: «Имеется проблема с сертификатом безопасности этого веб-сайта».  
  
Несмотря на то, что связь с помощью самозаверяющего сертификата шифрует обрабатываемых данных между клиентом и сервером, подключение осуществляется по-прежнему риску злоумышленниками.  
  
> [!WARNING]  
> Администраторы устройств должны немедленно получить сертификат, связанный доверенным центром сертификации распознается клиентами, для безопасного подключения и устранить эту ошибку, которая сообщает Internet Explorer.  
  
Путь сертификации должен содержать полное доменное имя, которое сопоставляется с узлом элемента управления (рекомендуется) IP-адрес кластера или имя, которое пользователи будут вводить в своих полосы адрес браузера для доступа к **консоли администрирования**.  
  
Используйте Analytics Platform System**Configuration Manager** Добавление и удаление доверенных сертификатов. Непосредственно с помощью средства конфигурации сертификата службы Microsoft Windows HTTP (**winHttpCertCfg.exe**) для управления сертификата не поддерживается.  
  
## <a name="import-or-remove-the-certificate"></a>Импортировать или удалить сертификат  
Ниже показано, как импорте и экспорте сертификата устройства.  
  
### <a name="to-import-the-certificate"></a>Чтобы импортировать сертификат  
  
1.  Запустите **Configuration Manager**. Дополнительные сведения см. в разделе [запустите диспетчер конфигурации &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой области **Configuration Manager**, разверните **топологии хранилища параллельных данных**, а затем нажмите кнопку **сертификаты**.  
  
3.  Выберите **импорта сертификата и настроить устройство для его использования**, а затем нажмите кнопку **Обзор** просмотреть и выбрать файл сертификата.  
  
4.  Введите пароль для сертификата в **пароль** поля.  
  
5.  Нажмите кнопку **применить** настроить сертификат для устройства.  
  
SQL Server PDW не зашифрует текущего соединения с помощью импортированный сертификат, но будет использовать сертификат для новых соединений.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>Чтобы удалить ранее импортированный сертификат  
  
1.  Запустите **Configuration Manager**. Дополнительные сведения см. в разделе [запустите диспетчер конфигурации &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой области **Configuration Manager**, разверните **топологии хранилища параллельных данных**, а затем нажмите кнопку **сертификаты**.  
  
3.  Выберите **удалить любой сертификат в устройстве**.  
  
4.  Нажмите кнопку **применить** для удаления ранее импортированный сертификат от устройства.  
  
SQL Server PDW продолжит шифрования текущих подключений, но не будет использовать сертификат удален для новых соединений.  
  
![Сертификат PDW DWConfig](./media/pdw-certificate-provisioning/SQL_Server_PDW_DWConfig_ApplPDWCert.png "SQL_Server_PDW_DWConfig_ApplPDWCert")  
  
## <a name="see-also"></a>См. также  
[Запустите диспетчер конфигурации &#40;система платформы аналитики&#41;](launch-the-configuration-manager.md)  
<!-- MISSING LINKS [HDInsight Certificate Provisioning &#40;Analytics Platform System&#41;](hdinsight-certificate-provisioning.md)  -->  
  
