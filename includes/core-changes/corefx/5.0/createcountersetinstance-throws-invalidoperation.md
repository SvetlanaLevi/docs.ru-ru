---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144489"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="4e463-101">Теперь CounterSet.CreateCounterSetInstance создает исключение InvalidOperationException, если экземпляр уже существует.</span><span class="sxs-lookup"><span data-stu-id="4e463-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="4e463-102">Начиная с .NET 5.0 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> создает исключение <xref:System.InvalidOperationException> вместо <xref:System.ArgumentException>, если набор счетчиков уже существует.</span><span class="sxs-lookup"><span data-stu-id="4e463-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4e463-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="4e463-103">Change description</span></span>

<span data-ttu-id="4e463-104">В .NET Framework и .NET Core 1.0–3.1 экземпляр набора счетчиков можно создать, вызвав <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e463-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="4e463-105">Однако если набор счетчиков уже существует, метод вызывает исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="4e463-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="4e463-106">В .NET 5.0 и более поздних версиях при вызове <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> и наличии набора счетчиков возникает исключение <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="4e463-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4e463-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="4e463-107">Version introduced</span></span>

<span data-ttu-id="4e463-108">5.0, предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="4e463-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e463-109">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="4e463-109">Recommended action</span></span>

<span data-ttu-id="4e463-110">Если при вызове <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> возникают исключения <xref:System.ArgumentException>, также следует рассмотреть перехват исключений <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="4e463-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="4e463-111">Перехват исключений <xref:System.ArgumentException> не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="4e463-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="4e463-112">Категория</span><span class="sxs-lookup"><span data-stu-id="4e463-112">Category</span></span>

<span data-ttu-id="4e463-113">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="4e463-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e463-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="4e463-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->