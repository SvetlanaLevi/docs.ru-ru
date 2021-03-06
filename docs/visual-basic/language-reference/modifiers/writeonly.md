---
description: 'Дополнительные сведения о: WriteOnly (Visual Basic)'
title: WriteOnly
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 514a1de3c8c2cfbde6a9cffc5c235d92454dd966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674744"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)

Указывает, что свойство может быть записано, но не прочитано.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="rules"></a>Правила  

 **Контекст объявления.** `WriteOnly` можно использовать только на уровне модуля. Это означает, что контекст объявления для `WriteOnly` свойства должен быть классом, структурой или модулем и не может быть исходным файлом, пространством имен или процедурой.  
  
 Можно объявить свойство как `WriteOnly` , но не переменную.  
  
## <a name="when-to-use-writeonly"></a>Когда следует использовать WriteOnly  

 Иногда требуется, чтобы в коде использовалась возможность задать значение, но не узнать, что это такое. Например, конфиденциальные данные, например номер социальной регистрации или пароль, должны быть защищены от доступа любым компонентом, который не задал его. В таких случаях `WriteOnly` для задания значения можно использовать свойство.  
  
> [!IMPORTANT]
> При определении и использовании `WriteOnly` Свойства учитывайте следующие дополнительные меры защиты:  
  
- **Переопределение.** Если свойство является членом класса, предоставьте ему значение по умолчанию [NotOverridable](notoverridable.md)и не объявляйте его `Overridable` или `MustOverride` . Это не позволяет производному классу делать нежелательный доступ с помощью переопределения.  
  
- **Уровень доступа.** Если конфиденциальные данные свойства хранятся в одной или нескольких переменных, объявите их [закрытыми](private.md) , чтобы другие коды не могли получить к ним доступ.  
  
- **Ключ.** Храните все конфиденциальные данные в зашифрованном виде, а не в виде обычного текста. Если вредоносный код каким-либо образом получает доступ к этой области памяти, более сложно использовать эти данные. Шифрование также полезно, если необходимо сериализовать конфиденциальные данные.  
  
- **Сброс.** При завершении работы класса, структуры или модуля, определяющего свойство, необходимо сбросить конфиденциальные данные на значения по умолчанию или другие бессмысленные значения. Это обеспечивает дополнительную защиту при освобождении области памяти для общего доступа.  
  
- **Сохраняемости.** Не следует сохранять конфиденциальные данные, например на диске, если это можно избежать. Кроме того, не записывайте конфиденциальные данные в буфер обмена.  
  
 `WriteOnly`Модификатор можно использовать в этом контексте:  
  
 [Property Statement](../statements/property-statement.md)  
  
## <a name="see-also"></a>См. также

- [ReadOnly](readonly.md)
- [Частная](private.md)
- [Ключевые слова](../keywords/index.md)
