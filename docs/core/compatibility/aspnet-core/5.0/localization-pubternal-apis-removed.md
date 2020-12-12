---
title: Критическое изменение. Удалены API-интерфейсы Pubternal
description: Сведения о критическом изменении в ASP.NET Core 5.0, где были удалены некоторые API локализации pubternal
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ae647d66b716175536edb3c978b027ebb7d3ddac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759658"
---
# <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="3c037-103">Локализация. Удалены API-интерфейсы Pubternal</span><span class="sxs-lookup"><span data-stu-id="3c037-103">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="3c037-104">Чтобы сохранить порядок в среде общедоступных API на платформе ASP.NET Core, некоторые API локализации :::no-loc text="\"pubternal\""::: были удалены.</span><span class="sxs-lookup"><span data-stu-id="3c037-104">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="3c037-105">API :::no-loc text="\"pubternal\""::: имеет модификатор доступа `public` и определен в пространстве имен, предполагающем использование намерения [internal](../../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="3c037-105">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="3c037-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="3c037-106">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3c037-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="3c037-107">Version introduced</span></span>

<span data-ttu-id="3c037-108">5.0, предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="3c037-108">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3c037-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="3c037-109">Old behavior</span></span>

<span data-ttu-id="3c037-110">Следующие API были `public`:</span><span class="sxs-lookup"><span data-stu-id="3c037-110">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="3c037-111">Перегрузки конструктора `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`, принимающие один из следующих типов параметров:</span><span class="sxs-lookup"><span data-stu-id="3c037-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a><span data-ttu-id="3c037-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="3c037-112">New behavior</span></span>

<span data-ttu-id="3c037-113">В следующем списке перечислены изменения.</span><span class="sxs-lookup"><span data-stu-id="3c037-113">The following list outlines the changes:</span></span>

- <span data-ttu-id="3c037-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` стал `Microsoft.Extensions.Localization.AssemblyWrapper` и теперь является `internal`.</span><span class="sxs-lookup"><span data-stu-id="3c037-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="3c037-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` стал `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` и теперь является `internal`.</span><span class="sxs-lookup"><span data-stu-id="3c037-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="3c037-116">Перегрузки конструктора `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`, принимающие один из следующих типов параметров, теперь являются `internal`:</span><span class="sxs-lookup"><span data-stu-id="3c037-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a><span data-ttu-id="3c037-117">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="3c037-117">Reason for change</span></span>

<span data-ttu-id="3c037-118">Более подробное описание приведено на странице [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), типы :::no-loc text="\"pubternal\""::: были удалены из области API `public`.</span><span class="sxs-lookup"><span data-stu-id="3c037-118">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="3c037-119">В соответствии с этими изменениями в процесс разработки можно включить больше классов.</span><span class="sxs-lookup"><span data-stu-id="3c037-119">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="3c037-120">Рассматриваемые классы предназначались для использования в качестве точек расширения для внутреннего тестирования команды.</span><span class="sxs-lookup"><span data-stu-id="3c037-120">The classes in question were intended as extension points for the team's internal testing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3c037-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="3c037-121">Recommended action</span></span>

<span data-ttu-id="3c037-122">Хотя это маловероятно, некоторые приложения могут намеренно или случайно зависеть от типов :::no-loc text="\"pubternal\"":::.</span><span class="sxs-lookup"><span data-stu-id="3c037-122">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="3c037-123">Сведения о переходе с конкретных типов см. в разделах [Новое поведение](#new-behavior).</span><span class="sxs-lookup"><span data-stu-id="3c037-123">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="3c037-124">Если возникла ситуация, в которой общедоступный API можно было использовать до этого изменения, а сейчас нельзя, разместите вопрос о проблеме на странице [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="3c037-124">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3c037-125">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="3c037-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->