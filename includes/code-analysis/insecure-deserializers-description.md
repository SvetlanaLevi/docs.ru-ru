---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 9235f1bcda7529b71aef542d3a49da08a9d4b59e
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592128"
---
<span data-ttu-id="b877e-101">Небезопасные десериализаторы уязвимы при десериализации ненадежных данных.</span><span class="sxs-lookup"><span data-stu-id="b877e-101">Insecure deserializers are vulnerable when deserializing untrusted data.</span></span> <span data-ttu-id="b877e-102">Злоумышленник может изменить сериализованные данные, чтобы включить непредвиденные типы для внедрения объектов с вредоносными побочными эффектами.</span><span class="sxs-lookup"><span data-stu-id="b877e-102">An attacker could modify the serialized data to include unexpected types to inject objects with malicious side effects.</span></span> <span data-ttu-id="b877e-103">Атака в небезопасном десериализаторе может, например, выполнять команды в базовой операционной системе, взаимодействовать по сети или удалять файлы.</span><span class="sxs-lookup"><span data-stu-id="b877e-103">An attack against an insecure deserializer could, for example, execute commands on the underlying operating system, communicate over the network, or delete files.</span></span>