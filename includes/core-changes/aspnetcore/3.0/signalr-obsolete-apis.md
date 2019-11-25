---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394462"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="fa0ee-101">SignalR: методы UseSignalR и UseConnections обозначены как устаревшие</span><span class="sxs-lookup"><span data-stu-id="fa0ee-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="fa0ee-102">Методы `UseConnections` и `UseSignalR`, а также классы `ConnectionsRouteBuilder` и `HubRouteBuilder` обозначены как устаревшие в ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fa0ee-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fa0ee-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="fa0ee-103">Version introduced</span></span>

<span data-ttu-id="fa0ee-104">3.0</span><span class="sxs-lookup"><span data-stu-id="fa0ee-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fa0ee-105">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="fa0ee-105">Old behavior</span></span>

<span data-ttu-id="fa0ee-106">Маршрутизация концентратора SignalR была настроена с помощью `UseSignalR` или `UseConnections`.</span><span class="sxs-lookup"><span data-stu-id="fa0ee-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fa0ee-107">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="fa0ee-107">New behavior</span></span>

<span data-ttu-id="fa0ee-108">Старый способ настройки маршрутизации считается устаревшим и был заменен маршрутизацией конечных точек.</span><span class="sxs-lookup"><span data-stu-id="fa0ee-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fa0ee-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="fa0ee-109">Reason for change</span></span>

<span data-ttu-id="fa0ee-110">ПО промежуточного слоя перемещается в новую систему маршрутизации конечных точек.</span><span class="sxs-lookup"><span data-stu-id="fa0ee-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="fa0ee-111">Старый способ добавления ПО промежуточного слоя считается устаревшим.</span><span class="sxs-lookup"><span data-stu-id="fa0ee-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fa0ee-112">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="fa0ee-112">Recommended action</span></span>

<span data-ttu-id="fa0ee-113">Замените `UseSignalR` на `UseEndpoints`:</span><span class="sxs-lookup"><span data-stu-id="fa0ee-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="fa0ee-114">**Старый код:**</span><span class="sxs-lookup"><span data-stu-id="fa0ee-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="fa0ee-115">**Новый код:**</span><span class="sxs-lookup"><span data-stu-id="fa0ee-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="fa0ee-116">Категория</span><span class="sxs-lookup"><span data-stu-id="fa0ee-116">Category</span></span>

<span data-ttu-id="fa0ee-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fa0ee-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fa0ee-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="fa0ee-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->