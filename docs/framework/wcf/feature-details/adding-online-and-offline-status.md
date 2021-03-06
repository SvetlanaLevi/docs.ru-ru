---
description: 'Дополнительные сведения: Добавление состояния в сети и вне сети'
title: Добавление подключенного и отключенного состояния
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 33f7920954ed28ebc2c3d34cc54a2e294f5730c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705243"
---
# <a name="adding-online-and-offline-status"></a>Добавление подключенного и отключенного состояния

Во многих случаях для приложения важно контролировать конкретные сведения о состоянии подключения по одноранговому каналу. Эти сведения можно получить, вызвав метод `GetProperty` в реализации интерфейса <xref:System.ServiceModel.IOnlineStatus>. Объект с реализацией этого интерфейса может контролировать состояние подключения или регистрировать обработчики событий, например `OnOnline` и `OnOffline`, и немедленно реагировать при возникновении изменений в состоянии подключения к сети.  
  
 В инфраструктуре одноранговых каналов клиент считается подключенным к сети, если он подключен по крайней мере к одному одноранговому узлу. В противном случае клиент считается автономным. Это может быть особенно полезно как при отладке разрабатываемых приложений, так и при отображении подробных сведений для конечного пользователя.  
  
> [!NOTE]
> Перед отправкой любых сообщений обработчик событий подключения к сети должен убедиться, что узел открыт.  
  
## <a name="see-also"></a>См. также

- [Создание приложения одноранговых каналов](building-a-peer-channel-application.md)
