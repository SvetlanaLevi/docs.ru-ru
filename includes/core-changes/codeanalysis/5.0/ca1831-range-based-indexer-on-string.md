---
ms.openlocfilehash: 4e937f56f6315ce2abf76dd56989f4d2c4059f22
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065196"
---
### <a name="ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a><span data-ttu-id="5901a-101">CA1831: используйте AsSpan вместо индексаторов на основе диапазона для строки</span><span class="sxs-lookup"><span data-stu-id="5901a-101">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>

<span data-ttu-id="5901a-102">Правило анализатора кода .NET [CA1831](/visualstudio/code-quality/ca1831) включено по умолчанию, начиная с .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="5901a-102">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="5901a-103">Оно создает предупреждение сборки для любого кода, в котором для строки используется индексатор на основе <xref:System.Range>, но копирование не планировалось.</span><span class="sxs-lookup"><span data-stu-id="5901a-103">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5901a-104">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="5901a-104">Change description</span></span>

<span data-ttu-id="5901a-105">Начиная с .NET 5.0, пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="5901a-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="5901a-106">Некоторые из этих правил включены по умолчанию, включая [CA1831](/visualstudio/code-quality/ca1831).</span><span class="sxs-lookup"><span data-stu-id="5901a-106">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="5901a-107">Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.</span><span class="sxs-lookup"><span data-stu-id="5901a-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="5901a-108">Правило CA1831 находит экземпляры, в которых для строки используется индексатор на основе <xref:System.Range>, но копирование не планировалось.</span><span class="sxs-lookup"><span data-stu-id="5901a-108">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="5901a-109">Если индексатор на основе <xref:System.Range> используется непосредственно в строке для создания неявного приведения, то создается ненужная копия запрошенной части строки.</span><span class="sxs-lookup"><span data-stu-id="5901a-109">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="5901a-110">Пример:</span><span class="sxs-lookup"><span data-stu-id="5901a-110">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="5901a-111">CA1831 предлагает использовать индексатор на основе <xref:System.Range> в *span* строки.</span><span class="sxs-lookup"><span data-stu-id="5901a-111">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="5901a-112">Пример:</span><span class="sxs-lookup"><span data-stu-id="5901a-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a><span data-ttu-id="5901a-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5901a-113">Version introduced</span></span>

<span data-ttu-id="5901a-114">5.0, предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="5901a-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5901a-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="5901a-115">Recommended action</span></span>

- <span data-ttu-id="5901a-116">Чтобы исправить код и избежать ненужных выделений, вызовите <xref:System.MemoryExtensions.AsSpan(System.String)> или <xref:System.MemoryExtensions.AsMemory(System.String)> перед использованием индексатора на основе <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="5901a-116">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="5901a-117">Пример:</span><span class="sxs-lookup"><span data-stu-id="5901a-117">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="5901a-118">Если вы не хотите изменять код, можно отключить правило, задав серьезность `suggestion` или `none`.</span><span class="sxs-lookup"><span data-stu-id="5901a-118">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="5901a-119">Дополнительные сведения см. в разделе [Настройка правил анализа кода](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span><span class="sxs-lookup"><span data-stu-id="5901a-119">For more information, see [Configure code analysis rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span></span>

- <span data-ttu-id="5901a-120">Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="5901a-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="5901a-121">Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="5901a-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="5901a-122">Категория</span><span class="sxs-lookup"><span data-stu-id="5901a-122">Category</span></span>

<span data-ttu-id="5901a-123">Анализ кода</span><span class="sxs-lookup"><span data-stu-id="5901a-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5901a-124">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5901a-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->