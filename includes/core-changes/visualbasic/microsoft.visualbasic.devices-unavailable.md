---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237443"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Типы из пространства имен Microsoft.VisualBasic.Devices недоступны

Типы в пространстве имен <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> недоступны.

#### <a name="version-introduced"></a>Представленная версия

.NET Core 3.0 (предварительная версия 8)

#### <a name="change-description"></a>Описание изменений

Типы из пространства имен <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> были доступны в некоторых предварительных выпусках .NET Core 3.0. Начиная с предварительной версии 9 .NET Core 3.0, они больше не доступны.

Типы были удалены во избежание ненужных зависимостей сборок или критических изменений в последующих выпусках.
 
#### <a name="recommended-action"></a>Рекомендуемое действие

Если в вашем коде применяются типы <xref:Microsoft.VisualBasic.Devices> и их члены, вы можете использовать соответствующий тип или член из библиотеки классов .NET. Например, возможности, эквивалентные классу <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType>, предоставляются типами <xref:System.DateTime?displayProperty=nameWithType> и <xref:System.Environment?displayProperty=nameWithType>, а классу <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> — типами в пространстве имен <xref:System.IO.Ports?displayProperty=nameWithType>.

#### <a name="category"></a>Категория

Visual Basic

#### <a name="affected-apis"></a>Затронутые API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >
