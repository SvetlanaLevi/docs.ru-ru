---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592131"
---
- <span data-ttu-id="9a7ac-101">Используйте вместо этого безопасный сериализатор и **не позволяйте злоумышленнику указывать произвольный тип для десериализации**.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-101">Use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="9a7ac-102">Дополнительные сведения см. в разделе [предпочтительные альтернативы](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).</span><span class="sxs-lookup"><span data-stu-id="9a7ac-102">For more information see the [Preferred alternatives](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).</span></span>
- <span data-ttu-id="9a7ac-103">Сделайте сериализованные данные несанкционированными.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-103">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="9a7ac-104">После сериализации криптографически подписывает сериализованные данные.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-104">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="9a7ac-105">Перед десериализациюм проверьте криптографическую подпись.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-105">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="9a7ac-106">Защитите криптографический ключ от раскрывать и разрабатывать для смены ключей.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-106">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
- <span data-ttu-id="9a7ac-107">Этот параметр делает код уязвимым к атакам типа "отказ в обслуживании" и возможным атакам удаленного выполнения кода в будущем.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-107">This option makes code vulnerable to denial of service attacks and possible remote code execution attacks in the future.</span></span> <span data-ttu-id="9a7ac-108">Дополнительные сведения см. в разделе [BinaryFormatter Security Guide](/dotnet/standard/serialization/binaryformatter-security-guide).</span><span class="sxs-lookup"><span data-stu-id="9a7ac-108">For more information, see the [BinaryFormatter security guide](/dotnet/standard/serialization/binaryformatter-security-guide).</span></span> <span data-ttu-id="9a7ac-109">Ограничьте десериализованные типы.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-109">Restrict deserialized types.</span></span> <span data-ttu-id="9a7ac-110">Реализуйте пользовательский интерфейс <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9a7ac-110">Implement a custom <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9a7ac-111">Перед десериализацией задайте `Binder` для свойства экземпляр пользовательского класса <xref:System.Runtime.Serialization.SerializationBinder> во всех путях кода.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-111">Before deserializing, set the `Binder` property to an instance of your custom <xref:System.Runtime.Serialization.SerializationBinder> in all code paths.</span></span> <span data-ttu-id="9a7ac-112">В переопределенном <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> методе, если тип является непредвиденным, вызовите исключение для отмены десериализации.</span><span class="sxs-lookup"><span data-stu-id="9a7ac-112">In the overridden <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> method, if the type is unexpected, throw an exception to stop deserialization.</span></span>