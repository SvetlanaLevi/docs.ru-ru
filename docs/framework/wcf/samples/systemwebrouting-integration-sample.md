---
description: 'Дополнительные сведения: пример интеграции Системвебраутинг'
title: Образец интеграции с SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 84b442dfb7f0e5877f742fb055aea49a5625bb78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668660"
---
# <a name="systemwebrouting-integration-sample"></a>Образец интеграции с SystemWebRouting

Этот образец показывает интеграцию уровня размещения с классами в пространстве имен <xref:System.Web.Routing>. Классы в пространстве имен <xref:System.Web.Routing> позволяют приложению использовать URL-адреса, которые не соответствуют непосредственно физическому ресурсу. Использование веб-маршрутизации позволяет разработчику создавать виртуальные адреса для протокола HTTP, которые затем сопоставляются с реальными службами WCF. Это может быть полезно, когда службу WCF необходимо разместить без обязательного выделения физического файла или ресурса или к службам необходимо получать доступ по URL-адресам, не содержащим файлов, например HTML или ASPX. Этот образец показывает использование класса <xref:System.Web.Routing.RouteTable> для создания виртуальных URI-адресов, связанных с выполняющимися службами, которые определены в файле global.asax.

> [!NOTE]
> Классы в пространстве имен <xref:System.Web.Routing> работают только со службами, размещаемыми по протоколу HTTP.  
  
В этом примере используется WCF для создания двух RSS-каналов: `movies` канала и `channels` канала. URL-адреса для активации служб не содержат расширения и регистрируются в `Application_Start` методе `Global` класса, производного от <xref:System.Web.HttpApplication> класса.  
  
> [!NOTE]
> Этот пример работает только в службы IIS (IIS) 7,0 и более поздних версиях, так как в IIS 6,0 используется другой метод для поддержки URL-адресов без расширений.  

#### <a name="to-download-this-sample"></a>Чтобы скачать этот пример
  
Возможно, этот образец уже установлен на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  

`<InstallDrive>:\WF_WCF_Samples`  

 Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Использование этого образца  
  
1. В Visual Studio откройте файл Вебраутингинтегратион. sln.  
  
2. Нажмите клавишу F5, чтобы выполнить решение и запустить веб-сервер разработки.  
  
     Отобразится список каталогов для образца. Обратите внимание, что файлы с расширением SVC отсутствуют.  
  
3. В адресной строке добавьте `movies` к URL-адресу, чтобы он был прочитан, `http://localhost:[port]/movies` и нажмите клавишу ВВОД.  
  
     В браузере откроется пакет фильмов.  
  
4. В адресной строке добавьте `channels` к URL-адресу, чтобы он был считан, `http://localhost:[port]/channels` и нажмите клавишу ВВОД.  
  
     В браузере откроется пакет каналов.  
  
5. Закройте веб-браузер, нажав клавиши ALT+F4.  
  
     Если сервер разработки не завершил работу, щелкните правой кнопкой мыши значок области уведомлений и выберите пункт **прекратить**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Использование этого образца в случае размещения на IIS  
  
1. В Visual Studio откройте файл Вебраутингинтегратион. sln.  
  
2. Постройте проект, нажав клавиши CTRL+SHIFT+B.  
  
3. Создайте веб-приложение в Диспетчере служб IIS.  
  
    1. В диспетчере служб IIS щелкните правой кнопкой мыши **веб-сайт по умолчанию** и выберите **Добавить приложение**.  
  
    2. В качестве **псевдонима** введите `WebRoutingIntegration` .  
  
    3. Для **физического пути** выберите папку службы внутри проекта.  
  
    4. Нажмите кнопку **ОК**.  
  
4. Запустите приложение, щелкнув правой кнопкой мыши веб-приложение и выбрав **Управление приложением** , а затем — **Обзор**.  
  
5. В адресной строке добавьте `movies` к URL-адресу, чтобы он был считан, `http://localhost:[port]/movies` и нажмите клавишу ВВОД.  
  
     В браузере откроется пакет фильмов.  
  
6. В адресной строке добавьте `channels` к URL-адресу, чтобы он был считан, `http://localhost:[port]/channels` и нажмите клавишу ВВОД.  
  
     В браузере откроется пакет каналов.  
  
7. Закройте веб-браузер, нажав клавиши ALT+F4.  
  
 Этот образец демонстрирует, что уровень размещения может взаимодействовать с классами в пространстве имен <xref:System.Web.Routing> для маршрутизации запросов служб, размещенных через протокол HTTP.  
  
> [!NOTE]
> Необходимо обновить версию пула приложений по умолчанию до платформа .NET Framework 4, если она имеет значение версии 2.  
  
## <a name="see-also"></a>См. также

- [Образцы размещения и сохраняемости AppFabric](/previous-versions/appfabric/ff383418(v=azure.10))
