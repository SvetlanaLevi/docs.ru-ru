---
title: Критическое изменение. Удалены элементы управления строкой состояния
description: Сведения о критических изменениях в .NET 5.0, где некоторые элементы управления Windows Forms больше не доступны.
ms.date: 07/18/2020
ms.openlocfilehash: 70aaa20f3fee1f4c342c4d9e547b0658aaf533b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759907"
---
# <a name="removed-status-bar-controls"></a><span data-ttu-id="c2f1d-103">Удалены элементы управления строкой состояния</span><span class="sxs-lookup"><span data-stu-id="c2f1d-103">Removed status bar controls</span></span>

<span data-ttu-id="c2f1d-104">Начиная с .NET 5.0 некоторые элементы управления Windows Forms больше не доступны.</span><span class="sxs-lookup"><span data-stu-id="c2f1d-104">Starting in .NET 5.0, some Windows Forms controls are no longer available.</span></span>

## <a name="change-description"></a><span data-ttu-id="c2f1d-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="c2f1d-105">Change description</span></span>

<span data-ttu-id="c2f1d-106">Начиная с .NET 5.0 некоторые элементы управления Windows Forms, связанные со строкой состояния, больше не доступны.</span><span class="sxs-lookup"><span data-stu-id="c2f1d-106">Starting with .NET 5.0, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="c2f1d-107">В .NET Framework 2.0 они были заменены элементами управления с улучшенной структурой и поддержкой.</span><span class="sxs-lookup"><span data-stu-id="c2f1d-107">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="c2f1d-108">Нерекомендуемые элементы управления были ранее удалены из панелей элементов конструктора, но по-прежнему были доступны для использования.</span><span class="sxs-lookup"><span data-stu-id="c2f1d-108">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="c2f1d-109">Теперь они окончательно удалены.</span><span class="sxs-lookup"><span data-stu-id="c2f1d-109">Now, they have been completely removed.</span></span>

<span data-ttu-id="c2f1d-110">Следующие типы больше не доступны.</span><span class="sxs-lookup"><span data-stu-id="c2f1d-110">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

## <a name="version-introduced"></a><span data-ttu-id="c2f1d-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c2f1d-111">Version introduced</span></span>

<span data-ttu-id="c2f1d-112">5.0</span><span class="sxs-lookup"><span data-stu-id="c2f1d-112">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c2f1d-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c2f1d-113">Recommended action</span></span>

<span data-ttu-id="c2f1d-114">Перейдите к замещающим API для этих элементов управления и их сценариев:</span><span class="sxs-lookup"><span data-stu-id="c2f1d-114">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="c2f1d-115">Старый элемент управления (API)</span><span class="sxs-lookup"><span data-stu-id="c2f1d-115">Old Control (API)</span></span> | <span data-ttu-id="c2f1d-116">Рекомендуемая замена</span><span class="sxs-lookup"><span data-stu-id="c2f1d-116">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="c2f1d-117">StatusBar</span><span class="sxs-lookup"><span data-stu-id="c2f1d-117">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="c2f1d-118">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="c2f1d-118">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

## <a name="affected-apis"></a><span data-ttu-id="c2f1d-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c2f1d-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle`

### Category

Windows Forms

-->