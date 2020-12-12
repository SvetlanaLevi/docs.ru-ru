---
title: Критическое изменение. В UNIX правильно анализируются пути URI с символами, отличными от ASCII
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где абсолютные пути URI, которые содержат символы, отличные от ASCII, теперь правильно анализируются на платформах UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 94de4e0eb94a11153d873871d4003422a4286a0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759629"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="1a6fc-103">В UNIX правильно анализируются пути URI с символами, отличными от ASCII</span><span class="sxs-lookup"><span data-stu-id="1a6fc-103">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="1a6fc-104">В классе <xref:System.Uri?displayProperty=fullName> была исправлена ошибка таким образом, что абсолютные пути URI, которые содержат символы, отличные от ASCII, теперь правильно анализируются на платформах UNIX.</span><span class="sxs-lookup"><span data-stu-id="1a6fc-104">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="1a6fc-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="1a6fc-105">Change description</span></span>

<span data-ttu-id="1a6fc-106">В предыдущих версиях .NET абсолютные пути URI, содержащие символы, отличные от ASCII, анализировались неправильно на платформах UNIX, а сегменты пути дублировались.</span><span class="sxs-lookup"><span data-stu-id="1a6fc-106">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="1a6fc-107">(Абсолютный путь — это путь, который начинается с "/".) Проблема анализа исправлена в .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="1a6fc-107">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="1a6fc-108">При переходе с предыдущей версии .NET на .NET 5.0 и более поздние версии вы получите различные значения, создаваемые <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType> и другими членами <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="1a6fc-108">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="1a6fc-109">Рассмотрим выходные данные следующего кода при выполнении в UNIX.</span><span class="sxs-lookup"><span data-stu-id="1a6fc-109">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="1a6fc-110">Выходные данные в предыдущей версии .NET:</span><span class="sxs-lookup"><span data-stu-id="1a6fc-110">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="1a6fc-111">Выходные данные в .NET 5.0 и более поздних версиях:</span><span class="sxs-lookup"><span data-stu-id="1a6fc-111">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a><span data-ttu-id="1a6fc-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1a6fc-112">Version introduced</span></span>

<span data-ttu-id="1a6fc-113">5.0</span><span class="sxs-lookup"><span data-stu-id="1a6fc-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1a6fc-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="1a6fc-114">Recommended action</span></span>

<span data-ttu-id="1a6fc-115">Если у вас есть код, который ожидает и учитывает повторяющиеся сегменты пути, то можно удалить этот код.</span><span class="sxs-lookup"><span data-stu-id="1a6fc-115">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1a6fc-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="1a6fc-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->