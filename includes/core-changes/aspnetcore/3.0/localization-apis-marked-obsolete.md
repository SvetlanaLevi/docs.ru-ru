---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393931"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="34f81-101">Локализация. ResourceManagerWithCultureStringLocalizer и WithCulture отмечены как устаревшие</span><span class="sxs-lookup"><span data-stu-id="34f81-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="34f81-102">Класс [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) и член-интерфейс [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) часто становились причиной путаницы для пользователей при локализации, особенно при создании собственной реализации `IStringLocalizer`.</span><span class="sxs-lookup"><span data-stu-id="34f81-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="34f81-103">Эти элементы создают у пользователей ощущение, что экземпляр `IStringLocalizer` создается отдельно для каждого языка и каждого ресурса.</span><span class="sxs-lookup"><span data-stu-id="34f81-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="34f81-104">На самом деле экземпляры различаются только для ресурсов.</span><span class="sxs-lookup"><span data-stu-id="34f81-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="34f81-105">Искомый язык определяется `CultureInfo.CurrentUICulture` во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="34f81-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="34f81-106">Чтобы устранить источник путаницы, эти API помечены как устаревшие в выпуске ASP.NET Core 3.0 предварительной версии 3.</span><span class="sxs-lookup"><span data-stu-id="34f81-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="34f81-107">Эти API будут удалены в будущем выпуске.</span><span class="sxs-lookup"><span data-stu-id="34f81-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="34f81-108">Контекст этого вопроса описан на странице [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="34f81-108">For context, see [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324).</span></span> <span data-ttu-id="34f81-109">Обсуждение этого вопроса см. на странице [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="34f81-109">For discussion, see [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="34f81-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="34f81-110">Version introduced</span></span>

<span data-ttu-id="34f81-111">3.0</span><span class="sxs-lookup"><span data-stu-id="34f81-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="34f81-112">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="34f81-112">Old behavior</span></span>

<span data-ttu-id="34f81-113">Методы не имели отметки `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="34f81-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="34f81-114">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="34f81-114">New behavior</span></span>

<span data-ttu-id="34f81-115">Методы получили отметку `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="34f81-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="34f81-116">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="34f81-116">Reason for change</span></span>

<span data-ttu-id="34f81-117">Эти API представляли нерекомендованный вариант использования.</span><span class="sxs-lookup"><span data-stu-id="34f81-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="34f81-118">Они создавали путаницу в отношении структуры локализации.</span><span class="sxs-lookup"><span data-stu-id="34f81-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="34f81-119">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="34f81-119">Recommended action</span></span>

<span data-ttu-id="34f81-120">Основная рекомендация: использовать вместо них `ResourceManagerStringLocalizer`.</span><span class="sxs-lookup"><span data-stu-id="34f81-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="34f81-121">Язык и региональные параметры должны устанавливаться в `CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="34f81-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="34f81-122">Если это невозможно, создайте и примените копию [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="34f81-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="34f81-123">Категория</span><span class="sxs-lookup"><span data-stu-id="34f81-123">Category</span></span>

<span data-ttu-id="34f81-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="34f81-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="34f81-125">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="34f81-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->