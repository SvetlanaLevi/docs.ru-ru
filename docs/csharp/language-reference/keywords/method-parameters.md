---
description: Справочник по C#. Параметры методов
title: Справочник по C#. Параметры методов
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 7090bf1c3df65cf1e65942404f883b49612e7521
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134410"
---
# <a name="method-parameters-c-reference"></a>Параметры методов (Справочник по C#)

Параметры, объявленные для метода без [in](./in-parameter-modifier.md), [ref](./ref.md) или [out](./out-parameter-modifier.md), передаются в вызываемый метод по значению. Это значение может изменяться в методе, однако измененное значение не будет сохраняться при возврате управления вызывающей процедуре. С помощью ключевого слова параметра метода это поведение можно изменить.  
  
 В этом разделе описываются ключевые слова, которые можно использовать при объявлении параметров метода:  
  
- [params](./params.md) указывает, что этот параметр может принимать переменное количество аргументов.
  
- [in](./in-parameter-modifier.md) указывает, что этот параметр передается по ссылке, но лишь считывается вызванным методом.
  
- [ref](./ref.md) указывает, что этот параметр передается по ссылке и может быть считан или записан вызванным методом.
  
- [out](./out-parameter-modifier.md) указывает, что этот параметр передается по ссылке и записывается вызванным методом.
  
## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](./index.md)
