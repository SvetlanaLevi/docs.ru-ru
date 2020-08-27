---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720212"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="e44a9-101">В UNIX правильно анализируются пути URI с символами, отличными от ASCII</span><span class="sxs-lookup"><span data-stu-id="e44a9-101">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="e44a9-102">В классе <xref:System.Uri?displayProperty=fullName> была исправлена ошибка таким образом, что абсолютные пути URI, которые содержат символы, отличные от ASCII, теперь правильно анализируются на платформах UNIX.</span><span class="sxs-lookup"><span data-stu-id="e44a9-102">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e44a9-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="e44a9-103">Change description</span></span>

<span data-ttu-id="e44a9-104">В предыдущих версиях .NET абсолютные пути URI, содержащие символы, отличные от ASCII, анализировались неправильно на платформах UNIX, а сегменты пути дублировались.</span><span class="sxs-lookup"><span data-stu-id="e44a9-104">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="e44a9-105">(Абсолютный путь — это путь, который начинается с "/".) Проблема анализа исправлена в .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="e44a9-105">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="e44a9-106">При переходе с предыдущей версии .NET на .NET 5.0 и более поздние версии вы получите различные значения, создаваемые <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType> и другими членами <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="e44a9-106">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="e44a9-107">Рассмотрим выходные данные следующего кода при выполнении в UNIX.</span><span class="sxs-lookup"><span data-stu-id="e44a9-107">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="e44a9-108">Выходные данные в предыдущей версии .NET:</span><span class="sxs-lookup"><span data-stu-id="e44a9-108">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="e44a9-109">Выходные данные в .NET 5.0 и более поздних версиях:</span><span class="sxs-lookup"><span data-stu-id="e44a9-109">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a><span data-ttu-id="e44a9-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e44a9-110">Version introduced</span></span>

<span data-ttu-id="e44a9-111">5.0</span><span class="sxs-lookup"><span data-stu-id="e44a9-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e44a9-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e44a9-112">Recommended action</span></span>

<span data-ttu-id="e44a9-113">Если у вас есть код, который ожидает и учитывает повторяющиеся сегменты пути, то можно удалить этот код.</span><span class="sxs-lookup"><span data-stu-id="e44a9-113">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

#### <a name="category"></a><span data-ttu-id="e44a9-114">Категория</span><span class="sxs-lookup"><span data-stu-id="e44a9-114">Category</span></span>

<span data-ttu-id="e44a9-115">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="e44a9-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e44a9-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e44a9-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->