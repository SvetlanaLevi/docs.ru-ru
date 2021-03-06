---
description: 'Дополнительные сведения о: Configuration-Based активации в IIS и WAS'
title: Активация на основе конфигурации в IIS и WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 7515e3f0d3035e1ab93c67980bd00eeb0a063d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743373"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Активация на основе конфигурации в IIS и WAS

Обычно при размещении службы Windows Communication Foundation (WCF) в службы IIS (IIS) или службе активации Windows (WAS) необходимо предоставить SVC-файл. SVC-файл содержит имя службы, а также дополнительную пользовательскую фабрику узла службы. С помощью этого дополнительного файла добавляются служебные данные по управлению. Возможность активации на основе конфигурации снимает требование по наличию SVC-файла и, следовательно, по наличию связанных служебных данных.

## <a name="configuration-based-activation"></a>Активация на основе конфигурации

Активация на основе конфигурации принимает метаданные, которые используются для размещения в SVC-файле, и помещает их в файл Web.config. В `serviceHostingEnvironment` элементе><имеется `serviceActivations` элемент <>. В элементе <`serviceActivations`> — один или несколько элементов <`add`>, по одному для каждой размещенной службы. `add`Элемент> <содержит атрибуты, позволяющие задать относительный адрес для службы, а также тип службы или фабрику узла службы. В следующем примере конфигурации показано, каким образом используется этот раздел.

> [!NOTE]
> Каждый `add` элемент> <должен указывать атрибут Service или Factory. Можно указать и атрибут службы, и атрибут фабрики.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 Такой код, показанный в файле Web.config, позволяет поместить исходный код службы в каталог App_Code приложения или откомпилированную сборку в каталог Bin приложения.

> [!NOTE]
>
> - При использовании активации на основе конфигурации, встроенный программный код в SVC-файлах не поддерживается.
> - `relativeAddress`Для атрибута необходимо задать относительный адрес, например " \<sub-directory> /сервице.СВК" или "~/ \< суб-директори/Service. svc".
> - Если зарегистрирован относительный адрес, который не содержит известного расширения имени, связанного с WCF, то будет создано исключение конфигурации.
> - Относительный адрес указывается относительно корневого каталога виртуального приложения.
> - Поскольку модель конфигурации имеет иерархическую структуру, относительный адрес, который зарегистрирован на уровне компьютера и узла, наследуется виртуальными приложениями.
> - Регистрация в файле конфигурации имеет более высокий приоритет, чем параметры в SVC-файле, XAMLX-файле, XOML-файле и других файлах.
> - Все символы обратной косой черты «\» в URI, отправляемых в IIS/WAS, автоматически преобразуются в символы косой черты «/». Если добавляемый относительный адрес содержит символ «\», а в IIS отправлен URI, который использует относительный адрес, то символ обратной косой черты преобразуется в символ косой черты и IIS не может сопоставить его с относительным адресом. Службы IIS отправляют сведения трассировки, которые указывают, что соответствие не найдено.

## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Размещение служб](../hosting-services.md)
- [Общие сведения о размещении служб рабочих процессов](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Функции размещения Windows Server App Fabric](/previous-versions/appfabric/ee677189(v=azure.10))
