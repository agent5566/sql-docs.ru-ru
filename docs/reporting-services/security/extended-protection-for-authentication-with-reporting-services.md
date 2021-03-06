---
title: Расширенная защита для проверки подлинности с использованием служб Reporting Services | Документы Майкрософт
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: security
ms.topic: conceptual
ms.assetid: eb5c6f4a-3ed5-430b-a712-d5ed4b6b9b2b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dec1019afa9363eafcc570e248736f518962abe7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682002"
---
# <a name="extended-protection-for-authentication-with-reporting-services"></a>Расширенная защита для проверки подлинности служб Reporting Services

  Расширенная защита — это набор усовершенствований, внесенных в последние версии операционной системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. С помощью расширенной защиты приложения могут лучше защищать учетные данные и проверку подлинности. Сама эта функция не обеспечивает защиту от определенных атак, например, таких как переадресация учетных данных, однако она предоставляет таким приложениям, как службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , инфраструктуру для ввода в действие расширенной защиты проверки подлинности.  
  
 Основными улучшениями процесса проверки подлинности, которые входят в расширенную защиту, являются привязка службы и привязка канала. Для привязки канала используется токен привязки канала (CBT), позволяющий удостовериться в целостности канала, установленного между двумя конечными точками. При привязке службы для проверки пункта назначения токенов проверки подлинности используются имена участников-служб (SPN). Дополнительные сведения о расширенной защите см. в разделе [Интегрированная проверка подлинности Windows с расширенной защитой](http://go.microsoft.com/fwlink/?LinkId=179922).  
  
Службы SQL Server Reporting Services поддерживают и поощряют использование расширенной защиты, включенной в операционной системе и настроенной в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. По умолчанию [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] принимает запросы, в которых указана проверка подлинности Negotiate или NTLM, что позволяет ему пользоваться поддержкой расширенной защиты в операционной системе и функциями расширенной защиты в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  По умолчанию расширенная защита в Windows отключена. Дополнительные сведения о включении расширенной защиты в Windows см. в разделе [Расширенная защита для проверки подлинности](http://go.microsoft.com/fwlink/?LinkID=178431). Для успешного прохождения проверки подлинности и операционная система, и стек проверки подлинности клиента должны поддерживать расширенную защиту. При использовании старых операционных систем для реализации на компьютере расширенной защиты может потребоваться установка нескольких обновлений. Сведения о последних изменениях, внесенных в расширенную защиту, см. в статье [Новые сведения о расширенной защите](http://go.microsoft.com/fwlink/?LinkId=183362).  

## <a name="reporting-services-extended-protection-overview"></a>Общие сведения о расширенной защите служб Reporting Services

Службы SSRS поддерживают и вводят в действие расширенную защиту, включенную в операционной системе. Если операционная система не поддерживает расширенную защиту или если эта функция в операционной системе отключена, то функция расширенной защиты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не сможет провести проверку подлинности. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] также требуется сертификат SSL. Дополнительные сведения см. в разделе [Настройка соединений SSL для сервера отчетов, работающего в собственном режиме](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
> [!IMPORTANT]  
>  По умолчанию в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] расширенная защита отключена. Эту функцию можно включить, изменив файл конфигурации **rsreportserver.config** или обновив этот файл с помощью средств WMI API. В службах SSRS нет пользовательского интерфейса для изменения или просмотра параметров расширенной защиты. Дополнительные сведения см. в разделе с описанием [параметров конфигурации](#ConfigurationSettings) в этой главе.  
  
 Обычные проблемы, возникающие из-за изменений параметров расширенной защиты или неверно заданных настроек, не сопровождаются понятными сообщениями об ошибках или диалоговыми окнами. Проблемы, связанные с конфигурацией расширенной защиты и совместимостью, ведут к возникновению сбоев при проверке подлинности и ошибок в журналах трассировки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Некоторые технологии доступа к данным могут не поддерживать расширенную защиту. Технология доступа к данным используется для подключения к источникам данных SQL Server и базе данных каталога служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Если технология доступа к данным не поддерживает расширенную защиту, это влияет на службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] следующим образом.  
>   
>  -   На SQL Server, на котором расположен каталог базы данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , нельзя включать расширенную защиту, в противном случае сервер отчетов не сможет подключиться к каталогу базы данных и будет возвращать ошибки проверки подлинности.  
> -   Ни на одном из серверов SQL Server, которые используются в качестве источников данных для отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , нельзя включать расширенную защиту, поскольку в случае ее включения попытки сервера отчетов подключиться к источнику данных для отчета завершатся неудачей и будут возвращены ошибки проверки подлинности.  
>   
>  В документации по технологии доступа к данным должны быть сведения о поддержке расширенной защиты.  
  
### <a name="upgrade"></a>UPGRADE  
  
-   При обновлении сервера служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] до версии SQL Server 2016 в файл **rsreportserver.config** добавляются параметры конфигурации со значениями по умолчанию. Если параметры уже имелись, то при установке SQL Server 2016 они будут сохранены в файле **rsreportserver.config**.  
  
-   По умолчанию при добавлении параметров конфигурации в файл конфигурации **rsreportserver.config** функция расширенной защиты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отключена. Ее необходимо включить, следуя описанной в этой главе процедуре. Дополнительные сведения см. в разделе с описанием [параметров конфигурации](#ConfigurationSettings) в этой главе.  
  
-   Значение по умолчанию для параметра **RSWindowsExtendedProtectionLevel** равно **Off**.  
  
-   Значение по умолчанию для параметра **RSWindowsExtendedProtectionScenario** равно **Proxy**.  
  
-   не проверяет, включена ли расширенная защита в операционной системе или текущей установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
### <a name="what-reporting-services-extended-protection-does-not-cover"></a>Какие службы Reporting Services не охватываются расширенной защитой  
 Следующие области и варианты не поддерживаются функцией расширенной защиты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
-   Авторы  настраиваемых модулей безопасности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] должны добавлять поддержку расширенной защиты в свои модули.  
  
-   Сторонние компоненты, добавленные в установку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или используемые ею, должны быть обновлены их поставщиками для обеспечения поддержки расширенной защиты. Обратитесь к сторонним поставщикам за дополнительными сведениями.  
  
## <a name="deployment-scenarios-and-recommendations"></a>Рекомендации и варианты развертывания  
 Описанные далее варианты иллюстрируют разные развертывания и топологии, а также рекомендуемые конфигурации для их защиты с помощью расширенной защиты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
### <a name="direct"></a>Прямой доступ  
 В этом сценарии описывается прямое соединение с сервером отчетов, например, в среде интрасети.  
  
|Сценарий|Диаграмма сценария|Инструкции по защите|  
|--------------|----------------------|-------------------|  
|Прямая связь по SSL.<br /><br /> Сервер отчетов принудит клиента использовать привязку канала сервера отчетов.|![RS_ExtendedProtection_DirectSSL](../../reporting-services/security/media/rs-extendedprotection-directssl.gif "RS_ExtendedProtection_DirectSSL")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов|Присвойте параметру **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Direct**.<br /><br /> <br /><br /> — Привязка службы не требуется, так как для привязки канала будет использоваться канал SSL.|  
|Прямая связь по HTTP. Сервер отчетов принудит клиента использовать привязку службы сервера отчетов.|![RS_ExtendedProtection_Direct](../../reporting-services/security/media/rs-extendedprotection-direct.gif "RS_ExtendedProtection_Direct")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов|Присвойте параметру **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Any**.<br /><br /> <br /><br /> — Канал SSL отсутствует, поэтому принудительно применить привязку канала невозможно.<br /><br /> Привязку службы можно проверить, однако такая защита привязки канала является неполной. Она способна защитить только от простых угроз.|  
  
### <a name="proxy-and-network-load-balancing"></a>Прокси и распределение сетевой нагрузки  
 Клиентские приложения подключаются к устройству или программному обеспечению, которое использует SSL и передает учетные данные серверу для проверки подлинности, например, в экстрасети, Интернете или защищенной интрасети. Клиент подключается к прокси или все клиенты используют прокси.  
  
 Такая же ситуация складывается при использовании устройства распределения сетевой нагрузки (NLB).  
  
|Сценарий|Диаграмма сценария|Инструкции по защите|  
|--------------|----------------------|-------------------|  
|Связь по HTTP. Сервер отчетов принудит клиента использовать привязку службы сервера отчетов.|![RS_ExtendedProtection_Indirect](../../reporting-services/security/media/rs-extendedprotection-indirect.gif "RS_ExtendedProtection_Indirect")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов<br /><br /> 3) Прокси|Присвойте параметру **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Any**.<br /><br /> <br /><br /> — Канал SSL отсутствует, поэтому принудительно применить привязку канала невозможно.<br /><br /> — В настройках сервера отчетов должно быть указано имя прокси-сервера, чтобы сервер отчетов мог принудительно применять привязку службы должным образом.|  
|Связь по HTTP.<br /><br /> Сервер отчетов принудит клиента использовать привязку канала прокси и привязку службы сервера отчетов.|![RS_ExtendedProtection_Indirect_SSL](../../reporting-services/security/media/rs-extendedprotection-indirect-ssl.gif "RS_ExtendedProtection_Indirect_SSL")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов<br /><br /> 3) Прокси|Присвойте параметру <br />                    **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Proxy**.<br /><br /> <br /><br /> — Доступен канал SSL к прокси-серверу, поэтому можно принудительно применить привязку канала к прокси-серверу.<br /><br /> — Привязку службы также можно принудительно применить.<br /><br /> — Серверу отчетов должно быть известно имя прокси-сервера, а администратор сервера отчетов должен либо создать для него резервирование URL-адреса с заголовком узла, либо указать имя прокси-сервера в записи реестра Windows **BackConnectionHostNames**.|  
|Непрямая связь по HTTPS с защищенным прокси. Сервер отчетов принудит клиента использовать привязку канала прокси и привязку службы сервера отчетов.|![RS_ExtendedProtection_IndirectSSLandHTTPS](../../reporting-services/security/media/rs-extendedprotection-indirectsslandhttps.gif "RS_ExtendedProtection_IndirectSSLandHTTPS")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов<br /><br /> 3) Прокси|Присвойте параметру <br />                    **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Proxy**.<br /><br /> <br /><br /> — Доступен канал SSL к прокси-серверу, поэтому можно принудительно применить привязку канала к прокси-серверу.<br /><br /> — Привязку службы также можно принудительно применить.<br /><br /> — Серверу отчетов должно быть известно имя прокси-сервера, а администратор сервера отчетов должен либо создать для него резервирование URL-адреса с заголовком узла, либо указать имя прокси-сервера в записи реестра Windows **BackConnectionHostNames**.|  
  
### <a name="gateway"></a>Шлюз  
 В этом сценарии клиентское приложение соединяется с устройством или программным обеспечением, использующим SSL и выполняющим проверку подлинности пользователя. Затем устройство или программное обеспечение олицетворяет контекст данного пользователя или контекст другого пользователя перед отправкой запроса серверу отчетов.  
  
|Сценарий|Диаграмма сценария|Инструкции по защите|  
|--------------|----------------------|-------------------|  
|Непрямая связь по HTTP.<br /><br /> Шлюз принудит клиента использовать привязку канала шлюза. На пути к привязке службы сервера отчетов имеется шлюз.|![RS_ExtendedProtection_Indirect_SSL](../../reporting-services/security/media/rs-extendedprotection-indirect-ssl.gif "RS_ExtendedProtection_Indirect_SSL")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов<br /><br /> 3) Шлюзовое устройство|Присвойте параметру **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Any**.<br /><br /> <br /><br /> — Привязка канала от клиента к серверу отчетов невозможна, так как шлюз олицетворяет контекст, т. е. создает новый маркер NTLM.<br /><br /> — На промежутке от шлюза до сервера отчетов нет SSL, поэтому принудительно применить привязку канала невозможно.<br /><br /> — Привязку службы можно принудительно применить.<br /><br /> — Администратор должен настроить для устройства шлюза принудительное применение привязки канала.|  
|Непрямая связь по HTTPS с защищенным шлюзом. Шлюз принудит клиента использовать привязку канала шлюза, а сервер отчетов принудит шлюз использовать привязку канала сервера отчетов.|![RS_ExtendedProtection_IndirectSSLandHTTPS](../../reporting-services/security/media/rs-extendedprotection-indirectsslandhttps.gif "RS_ExtendedProtection_IndirectSSLandHTTPS")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов<br /><br /> 3) Шлюзовое устройство|Присвойте параметру **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Direct**.<br /><br /> <br /><br /> — Привязка канала от клиента к серверу отчетов невозможна, так как шлюз олицетворяет контекст, т. е. создает новый маркер NTLM.<br /><br /> — Наличие SSL на промежутке от шлюза до сервера отчетов означает, что можно принудительно применить привязку канала.<br /><br /> — Привязка службы не требуется.<br /><br /> — Администратор должен настроить для устройства шлюза принудительное применение привязки канала.|  
  
### <a name="combination"></a>Сочетание  
 В этом сценарии описывается экстрасеть или Интернет в ситуации, когда клиент устанавливает соединение с прокси. Происходит это в сочетании со средой интрасети, в которой клиент устанавливает соединение с сервером отчетов.  
  
|Сценарий|Диаграмма сценария|Инструкции по защите|  
|--------------|----------------------|-------------------|  
|Непрямой и прямой доступ от клиента к службе сервера отчетов без SSL по каналу между клиентом и прокси или клиентом и сервером отчетов.|1) Клиентское приложение<br /><br /> 2) Сервер отчетов<br /><br /> 3) Прокси<br /><br /> 4) Клиентское приложение|Присвойте параметру **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Any**.<br /><br /> <br /><br /> — Привязку службы от клиента к серверу отчетов можно принудительно применить.<br /><br /> — Серверу отчетов должно быть известно имя прокси-сервера, а администратор сервера отчетов должен либо создать для него резервирование URL-адреса с заголовком узла, либо указать имя прокси-сервера в записи реестра Windows **BackConnectionHostNames**.|  
|Непрямой и прямой доступ от клиента к серверу отчетов, когда клиент устанавливает соединение SSL с прокси или сервером отчетов.|![RS_ExtendedProtection_CombinationSSL](../../reporting-services/security/media/rs-extendedprotection-combinationssl.gif "RS_ExtendedProtection_CombinationSSL")<br /><br /> 1) Клиентское приложение<br /><br /> 2) Сервер отчетов<br /><br /> 3) Прокси<br /><br /> 4) Клиентское приложение|Присвойте параметру **RSWindowsExtendedProtectionLevel** значение **Allow** или **Require**.<br /><br /> Присвойте параметру **RSWindowsExtendedProtectionScenario** значение **Proxy**.<br /><br /> <br /><br /> — Можно использовать привязку канала.<br /><br /> — Серверу отчетов должно быть известно имя прокси-сервера, а администратор сервера отчетов должен либо создать для прокси-сервера резервирование URL-адреса с заголовком узла, либо указать имя прокси-сервера в записи реестра Windows **BackConnectionHostNames**.|  
  
## <a name="configuring-reporting-rervices-extended-protection"></a>Настройка расширенной защиты служб Reporting Services  
 Файл **rsreportserver.config** содержит значения конфигурации, управляющие поведением расширенной защиты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Дополнительные сведения об использовании и изменении файла **rsreportserver.config** см. в разделе [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md). Параметры расширенной защиты также можно изменить и просмотреть с помощью средств WMI API. Дополнительные сведения см. в разделе [Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md).  
  
 Если параметры конфигурации не проходят проверку, на сервере отчетов отключаются типы проверки подлинности **RSWindowsNTLM**, **RSWindowsKerberos** и **RSWindowsNegotiate** .  
  
###  <a name="ConfigurationSettings"></a> Параметры конфигурации для расширенной защиты служб Reporting Services  
 В следующей таблице приведены сведения о параметрах конфигурации, приведенных в файле **rsreportserver.config** для расширенной защиты.  
  
|Настройка|Описание|  
|-------------|-----------------|  
|**RSWindowsExtendedProtectionLevel**|Указывает степень использования расширенной защиты. Допустимые значения:<br /><br /> **Off**: по умолчанию. Указывает на отсутствие проверки привязки канала или привязки службы.<br /><br /> **Allow** означает, что расширенная защита поддерживается, при этом она не является обязательной.  Указывает следующее.<br /><br /> — Расширенная защита будет принудительно применяться для клиентских приложений, работающих в операционных системах, которые поддерживают расширенную защиту. Способ принудительного применения защиты определяется параметром **RsWindowsExtendedProtectionScenario**.<br /><br /> — Аутентификация будет разрешена для приложений, работающих в операционных системах, которые не поддерживают расширенную защиту.<br /><br /> Значение**Require** указывает следующее.<br /><br /> — Расширенная защита будет принудительно применяться для клиентских приложений, работающих в операционных системах, которые поддерживают расширенную защиту.<br /><br /> — Аутентификация **не** будет разрешена для приложений, работающих в операционных системах, которые не поддерживают расширенную защиту.|  
|**RsWindowsExtendedProtectionScenario**|Указывает, какие формы расширенной защиты проверяются: привязка канала, привязка службы или то и другое. Допустимые значения:<br /><br /> **Proxy**: по умолчанию. Указывает следующее.<br /><br /> — Аутентификация Windows NTLM, Kerberos и Negotiate при наличии маркера привязки канала.<br /><br /> — Привязка службы применяется принудительно.<br /><br /> Значение**Any** указывает следующее.<br /><br /> — Аутентификация Windows NTLM, Kerberos и Negotiate и привязка канала не требуется.<br /><br /> — Привязка службы применяется принудительно.<br /><br /> Значение**Direct** указывает следующее.<br /><br /> — Аутентификация Windows NTLM, Kerberos и Negotiate при наличии компьютеризованного обучения, соединения SSL с текущей службой и совпадении компьютеризованного обучения для соединения SSL с компьютеризованным обучением маркера NTLM, Kerberos или Negotiate.<br /><br /> — Привязка службы не применяется принудительно.<br /><br /> <br /><br /> Примечание. Параметр **RsWindowsExtendedProtectionScenario** не учитывается, если параметру **RsWindowsExtendedProtectionLevel** присвоено значение **OFF**.|  
  
 Образцы записей из файла конфигурации **rsreportserver.config** :  
  
```  
<Authentication>  
         <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>  
         <RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionLevel>  
</Authentication>  
```  
  
## <a name="service-binding-and-included-spns"></a>Привязка службы и включенные SPN  
 Привязка службы использует для проверки пункта назначения токенов проверки подлинности имена участников-служб (SPN). [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] используют сведения о существующем резервировании URL-адресов для создания списка допустимых SPN. Благодаря использованию сведений резервирования URL-адреса для проверки и SPN и резервирования URL-адреса системные администраторы могут управлять обеими проверками из одного места.  
  
 Список действующих SPN обновляется при запуске сервера отчетов, при изменении параметров конфигурации расширенной защиты или при очистке домена приложений.  
  
 У каждого из приложений — свой список допустимых SPN. Например, диспетчер отчетов и сервер отчетов будут вычислять разные списки допустимых SPN.  
  
 Список допустимых SPN, вычисляемый для приложения, определяется следующими факторами:  
  
-   Каждое резервирование URL-адресов.  
  
-   Каждый SPN, полученный от контроллера домена для учетной записи служб Reporting Services.  
  
-   Если в резервировании URL-адреса есть символы-шаблоны («*» или «+»), то сервер отчетов добавит каждую запись из коллекции узлов.  
  
### <a name="hosts-collection-sources"></a>Источники коллекции узлов.  
 В следующей таблице перечислены потенциальные источники для коллекции узлов.  
  
|Тип источника|Описание|  
|--------------------|-----------------|  
|ComputerNameDnsDomain|Имя домена DNS, назначенное локальному компьютеру. Если локальный компьютер является узлом или кластером, используется доменное имя DNS виртуального сервера кластера.|  
|ComputerNameDnsFullyQualified|Полное имя DNS, служащее уникальным идентификатором локального компьютера. Это имя является сочетанием имени узла DNS и доменного имени DNS и имеет форму *ИмяУзла*.*ИмяДомена*. Если локальный компьютер является узлом или кластером, используется полное имя DNS виртуального сервера кластера.|  
|ComputerNameDnsHostname|Имя узла DNS локального компьютера. Если локальный компьютер является узлом или кластером, используется имя узла DNS виртуального сервера кластера.|  
|ComputerNameNetBIOS|Имя NetBIOS локального компьютера. Если локальный компьютер является узлом или кластером, используется имя NetBIOS виртуального сервера кластера.|  
|ComputerNamePhysicalDnsDomain|Имя домена DNS, назначенное локальному компьютеру. Если локальный компьютер является узлом или кластером, используется доменное имя DNS локального компьютера, а не виртуального сервера кластера.|  
|ComputerNamePhysicalDnsFullyQualified|Полное имя DNS, служащее уникальным идентификатором компьютера. Если локальный компьютер является узлом или кластером, используется полное имя DNS локального компьютера, а не виртуального сервера кластера.<br /><br /> Полное имя DNS является сочетанием имени узла DNS и доменного имени DNS и имеет форму *ИмяУзла*.*ИмяДомена*.|  
|ComputerNamePhysicalDnsHostname|Имя узла DNS локального компьютера. Если локальный компьютер является узлом или кластером, используется имя узла DNS локального компьютера, а не виртуального сервера кластера.|  
|ComputerNamePhysicalNetBIOS|Имя NetBIOS локального компьютера. Если локальный компьютер является узлом или кластером, используется имя NetBIOS локального компьютера, а не виртуального сервера кластера.|  
  
 По мере добавления SPN в журнал трассировки заносится запись, аналогичная следующей:  
  
 `rshost!rshost!10a8!01/07/2010-19:29:38:: i INFO: SPN Whitelist Added <ComputerNamePhysicalNetBIOS> - <theservername>.`  
  
 `rshost!rshost!10a8!01/07/2010-19:29:38:: i INFO: SPN Whitelist Added <ComputerNamePhysicalDnsHostname> - <theservername>.`  
  
 Дополнительные сведения см. в статьях [Регистрация имени участника-службы для сервера отчетов](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md) и [Сведения о резервировании и регистрации URL-адресов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/about-url-reservations-and-registration-ssrs-configuration-manager.md).  
  
## <a name="next-steps"></a>Следующие шаги

[Соединение с компонентом Database Engine с использованием расширенной защиты](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)   
[Общие сведения о расширенной защите для проверки подлинности](http://go.microsoft.com/fwlink/?LinkID=177943)   
[Интегрированная проверка подлинности Windows с расширенной защитой](http://go.microsoft.com/fwlink/?LinkId=179922)   
[Советы корпорации Майкрософт по безопасности: расширенная защита для проверки подлинности](http://go.microsoft.com/fwlink/?LinkId=179923)   
[Журнал трассировки службы сервера отчетов](../../reporting-services/report-server/report-server-service-trace-log.md)   
[Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
