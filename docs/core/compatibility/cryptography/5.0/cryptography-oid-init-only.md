---
title: Критическое изменение. Класс Cryptography.Oid функционально доступен только для инициализации
description: Сведения о критическом изменении в .NET 5.0, где методы задания свойств в классе Cryptography.Oid теперь вызывают исключение при попытке изменить значение.
ms.date: 08/16/2020
ms.openlocfilehash: a3b5a393e2a84f7c9a60c2a821ecfda9c6acd2e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759649"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="c904a-103">Класс System.Security.Cryptography.Oid функционально доступен только для инициализации</span><span class="sxs-lookup"><span data-stu-id="c904a-103">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="c904a-104">Класс <xref:System.Security.Cryptography.Oid?displayProperty=fullName>, используемый для представления значений идентификаторов объектов ASN.1 и их понятных имен, был ранее полностью изменяемым.</span><span class="sxs-lookup"><span data-stu-id="c904a-104">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="c904a-105">Эта изменяемость часто игнорировалась или становилась неожиданностью.</span><span class="sxs-lookup"><span data-stu-id="c904a-105">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="c904a-106">Теперь методы задания свойств вызывают <xref:System.PlatformNotSupportedException> при попытке изменить значение после того, как оно уже было назначено.</span><span class="sxs-lookup"><span data-stu-id="c904a-106">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

## <a name="change-description"></a><span data-ttu-id="c904a-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="c904a-107">Change description</span></span>

<span data-ttu-id="c904a-108">В предыдущих версиях методы задания свойств в <xref:System.Security.Cryptography.Oid> можно было использовать для изменения значений свойств <xref:System.Security.Cryptography.Oid.FriendlyName> и <xref:System.Security.Cryptography.Oid.Value>.</span><span class="sxs-lookup"><span data-stu-id="c904a-108">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="c904a-109">В .NET 5.0 и более поздних версиях методы задания свойств можно использовать только для инициализации значения.</span><span class="sxs-lookup"><span data-stu-id="c904a-109">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="c904a-110">После того как свойство получило значение из конструктора или предыдущего вызова метода задания свойств, метод задания свойств всегда будет вызывать <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="c904a-110">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c904a-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="c904a-111">Reason for change</span></span>

<span data-ttu-id="c904a-112">Это изменение позволяет повторно использовать объекты <xref:System.Security.Cryptography.Oid> как часть возвращаемых значений в общедоступных API для уменьшения количества профилей выделения объектов.</span><span class="sxs-lookup"><span data-stu-id="c904a-112">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="c904a-113">Это позволяет избежать необходимости создавать временные "защитные" копии, когда значения <xref:System.Security.Cryptography.Oid> используются в качестве входных данных.</span><span class="sxs-lookup"><span data-stu-id="c904a-113">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c904a-114">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c904a-114">Version introduced</span></span>

<span data-ttu-id="c904a-115">5.0</span><span class="sxs-lookup"><span data-stu-id="c904a-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c904a-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c904a-116">Recommended action</span></span>

<span data-ttu-id="c904a-117">Избегайте использования методов задания свойств <xref:System.Security.Cryptography.Oid>, отличных от инициализации объектов.</span><span class="sxs-lookup"><span data-stu-id="c904a-117">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="c904a-118">Чтобы представить новое значение, используйте новый экземпляр вместо изменения значения существующего объекта.</span><span class="sxs-lookup"><span data-stu-id="c904a-118">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c904a-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c904a-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->