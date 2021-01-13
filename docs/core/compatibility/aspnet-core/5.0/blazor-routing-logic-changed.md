---
title: 'Критическое изменение. Blazor: Изменения в логике маршрутизации в приложениях Blazor'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Изменения в логике маршрутизации в приложениях Blazor
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513511"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a>Blazor: в приложениях изменена логика очередности маршрутов

Ошибка в реализации маршрутизации Blazor влияет на порядок определения приоритета маршрутов. Эта ошибка влияет на все маршруты перехвата или маршруты с необязательными параметрами в приложении Blazor.

## <a name="version-introduced"></a>Представленная версия

5.0.1

## <a name="old-behavior"></a>Старое поведение

При ошибочном поведении маршруты с более низким приоритетом рассматриваются и сопоставляются с маршрутами с более высоким приоритетом. Например, маршрут `{*slug}` сопоставляется до `/customer/{id}`.

## <a name="new-behavior"></a>Новое поведение

Текущее поведение более близко соответствует поведению маршрутизации, определенному в приложениях ASP.NET Core. Платформа сначала определяет приоритет маршрута для каждого сегмента. Длина маршрута используется только в качестве второго критерия для разрыва связей.

## <a name="reason-for-change"></a>Причина изменения

Исходное поведение считается ошибкой в реализации. Система маршрутизации в приложениях Blazor должна вести себя так же, как и система маршрутизации в остальной части ASP.NET Core.

## <a name="recommended-action"></a>Рекомендованное действие

При обновлении с предыдущих версий Blazor до версии 5.x используйте атрибут `PreferExactMatches` в компоненте `Router`. Этот атрибут можно использовать для выбора правильного поведения. Пример:

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

Если `PreferExactMatches` имеет значение `true`, то при сопоставлении маршрутов предпочтение отдается точным совпадениям, а не подстановочным знакам.

## <a name="affected-apis"></a>Затронутые API

None

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->