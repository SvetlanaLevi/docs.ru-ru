---
title: Директива x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2020
ms.locfileid: "81432788"
---
# <a name="xfactorymethod-directive"></a>Директива x:FactoryMethod
Определяет метод, отличный от конструктора, который процессор XAML должен использовать для инициализации объекта после разрешения его типа резервного копирования.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Использование атрибутов XAML, без x:Аргументы  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Использование атрибутов XAML, x:Аргументы как элемент (ы)  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Значения XAML  
  
|||  
|-|-|  
|`methodname`|Название метода строки метода, который процессоры XAML `object`называют для инициализации экземпляра, указанного как. См. заметки.|  
|`oneOrMoreObjectElements`|Один или несколько элементов объекта для объектов, определяющих параметры фабричного метода. Порядок значителен; он означает порядок, в котором аргументы должны быть переданы на заводский метод.|  
  
## <a name="remarks"></a>Примечания  
 Если `methodname` это метод экземпляра, он не может быть квалифицирован.  
  
 Поддержку используются статические методы в качестве фабричных методов. Если `methodname` это статический `methodname` метод, `typeName.methodName` предоставляется `typeName` как комбинация, где называется класс, определяющий метод статической фабрики. `typeName`может быть приставка-квалифицированных, если речь идет о типе в отображеном xmlns. `typeName`может быть другого `typeof(object)`типа, чем .  
  
 Метод завода должен быть заявленным общедоступным методом типа, который поддерживает соответствующий элемент объекта.  
  
 Метод фабрики должен вернуть экземпляр, присвоенный соответствующему объекту. Заводские методы никогда не должны возвращатьнули.  
  
 `x:Arguments`работает по принципу лучшего соответствия для подписи заводских методов. Соответствие оценивает количество параметров в первую очередь. Если существует более одного возможного совпадения для подсчета параметров, тип параметра затем оценивается и определяется лучший матч. Если после этого этапа оценки все еще существует двусмысленность, поведение процессора XAML не определено.  
  
 Использование `x:FactoryMethod` элемента не является использованием элемента свойства в типичном смысле, поскольку разметка директивы не ссылается на тип элемента, содержащего объект. Ожидается, что использование элементов встречается реже, чем использование атрибутов. `x:Arguments`(или атрибут или использование элемента) `x:FactoryMethod` могут быть использованы вместе с использованием элементов, но это не конкретно показано в разделах использования.  
  
 `x:FactoryMethod`как элемент должен предшествовать любым другим элементам `x:Arguments` свойства, должен предшествовать любому также представленному в качестве элементов, и должен предшествовать любому содержанию/внутреннему тексту/тексту инициализации.  
  
## <a name="see-also"></a>См. также

- [Директива x:Arguments](xarguments-directive.md)