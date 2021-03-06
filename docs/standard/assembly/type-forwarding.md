---
title: Переадресация типов в общеязыковой среде CLR
description: Перенаправление типа позволяет переместить тип в другую сборку .NET без повторной компиляции приложений, использующих исходную сборку.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687668"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Переадресация типов в общеязыковой среде CLR

Перенаправление типа позволяет переместить тип в другую сборку без повторной компиляции приложений, использующих исходную сборку.  
  
 Предположим, например, что приложение использует класс `Example` в сборке с именем *Utility.dll*. Разработчики *Utility.dll* могут принять решение выполнить рефакторинг сборки и в ходе этого процесса могут переместить класс `Example` в другую сборку. Если старую версию *Utility.dll* заменить новой версией *Utility.dll* и ее сопутствующей сборкой, приложение, использующее класс `Example`, завершится ошибкой, так как не сможет найти класс `Example` в новой версии *Utility.dll*.  
  
 Разработчики *Utility.dll* могут избежать этого, перенаправляя запросы к классу `Example` с помощью атрибута <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>. Если атрибут применен к новой версии *Utility.dll* , запросы класса `Example` перенаправляются в сборку, которая теперь содержит этот класс. Существующее приложение продолжает нормально функционировать без перекомпиляции.

## <a name="forward-a-type"></a>Перенаправление типа

 Для перенаправления типа следует выполнить следующую процедуру.  
  
1. Переместите исходный код для типа из исходной сборки в целевую сборку.  

2. В сборке, где раньше находился тип, добавьте <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> для типа, который был перемещен. В следующем коде показан атрибут для типа с именем `Example`, который был перемещен.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Скомпилируйте сборку, которая теперь содержит тип.  

4. Перекомпилируйте сборку, где раньше находился тип, со ссылкой на сборку, которая теперь содержит тип. Например, при компиляции файла C# из командной строки используйте параметр [-reference (параметры компилятора C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md), чтобы указать сборку, содержащую тип. В C++ используйте директиву [#using](/cpp/preprocessor/hash-using-directive-cpp) в исходном файле, чтобы указать сборку, содержащую тип.  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Перенаправление типов (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [Директива #using](/cpp/preprocessor/hash-using-directive-cpp)
