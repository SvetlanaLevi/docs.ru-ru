---
title: Разработка перечислений
description: Разработка для перечислений, которые являются специальным видом типа значения. Простые перечисления содержат небольшие закрытые наборы вариантов выбора. Флаговые перечисления поддерживают побитовые операции с перечисляемыми значениями.
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: a2e19197b114daa2a0956a6fc87231a6a81de916
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821363"
---
# <a name="enum-design"></a>Разработка перечислений

Перечисления являются особым видом типа значения. Существует два вида перечислений: Простые перечисления и Флаговые перечисления.

Простые перечисления представляют небольшие закрытые наборы вариантов выбора. Распространенным примером простого перечисления является набор цветов.

Перечисление флагов предназначено для поддержки побитовых операций над значениями перечисления. Распространенным примером перечисления Flags является список параметров.

✔️ использовать перечисление для строго типизированных параметров, свойств и возвращаемых значений, представляющих наборы значений.

✔️ предпочитаете использовать перечисление вместо статических констант.

❌ НЕ используйте перечисление для открытых наборов (таких как версия операционной системы, имена друзей и т. д.).

❌ НЕ предоставляющих зарезервированные значения перечисления, предназначенные для будущего использования.

Вы всегда можете просто добавить значения к существующему перечислению на более позднем этапе. Дополнительные сведения о добавлении значений в перечисления см. в разделе [Добавление значений в перечисления](#add_value) . Зарезервированные значения просто засоряла набор реальных значений и обычно ведут к ошибкам пользователя.

❌ Старайтесь не использовать в открытых перечислениях только одно значение.

Распространенной практикой для обеспечения будущего расширяемости C API является добавление зарезервированных параметров в сигнатуры методов. Такие зарезервированные параметры могут быть выражены как перечисления с одним значением по умолчанию. Это не следует делать в управляемых API. Перегрузка метода позволяет добавлять параметры в будущих выпусках.

❌ НЕ включайте значения Sentinel в перечисления.

Хотя иногда они полезны разработчикам платформ, значения меток могут сбить с толку пользователей платформы. Они используются для отслеживания состояния перечисления, а не одного из значений набора, представленного перечислением.

✔️ предоставить нулевое значение для простых перечислений.

Попробуйте вызвать значение, например "нет". Если такое значение не подходит для этого конкретного перечисления, то наиболее распространенному значению перечисления по умолчанию должно быть присвоено базовое значение, равное нулю.

✔️ РЕКОМЕНДУЕТСЯ использовать <xref:System.Int32> (по умолчанию в большинстве языков программирования) в качестве базового типа перечисления, если не выполняется какое-либо из следующих условий.

- Перечисление является перечислением Flags и имеет более 32 флагов или может быть больше в будущем.

- Базовый тип должен отличаться от типа <xref:System.Int32> для упрощения взаимодействия с неуправляемым кодом, ожидающим перечисления разного размера.

- Базовый тип меньшего размера приведет к значительному экономии пространства. Если предполагается, что перечисление будет использоваться в основном как аргумент для потока управления, размер делает незначительную разницу. Экономия размера может быть значительной, если:

  - Предполагается, что перечисление будет использоваться в качестве поля в очень часто создаваемой структуре или классе.

  - Предполагается, что пользователи будут создавать большие массивы или коллекции экземпляров перечисления.

  - Предполагается, что будет сериализовано большое количество экземпляров перечисления.

При использовании в памяти следует помнить, что управляемые объекты всегда являются `DWORD` согласованными, поэтому в экземпляре необходимо использовать несколько перечислений или другие небольшие структуры для упаковки меньшего перечислимого типа с целью создания разницы, так как общий размер экземпляра всегда будет округляться вплоть до `DWORD` .

✔️ флаги имени перечисления с существительными во множественном числе или субстантивные словосочетаниями и простыми перечислениями с существительными или существительными в единственном числе.

❌ НЕ расширяйте их <xref:System.Enum?displayProperty=nameWithType> напрямую.

<xref:System.Enum?displayProperty=nameWithType> — Это специальный тип, используемый средой CLR для создания определяемых пользователем перечислений. Большинство языков программирования предоставляют программный элемент, обеспечивающий доступ к этой функции. Например, в C# `enum` для определения перечисления используется ключевое слово.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Разработка перечислений флагов

✔️ применить <xref:System.FlagsAttribute?displayProperty=nameWithType> к перечислениям флаги. Не применяйте этот атрибут к простым перечислениям.

✔️ использовать степени двух для флаговых значений enum, чтобы их можно было свободно комбинировать с помощью побитовой операции или.

✔️ Рассмотрите возможность предоставления специальных перечислимых значений для часто используемых сочетаний флагов.

Битовые операции являются сложной концепцией и не должны требоваться для простых задач. <xref:System.IO.FileAccess.ReadWrite> Пример такого специального значения.

❌ Избегайте создания перечислений флагов, в которых некоторые сочетания значений недопустимы.

❌ СТАРАЙТЕСЬ не использовать флаги нулевых значений, если только значение не представляет «все флаги сняты» и имеет соответствующее имя, как указано в следующей рекомендации.

✔️ Присвойте нулевое значение для перечислений Flag `None` . Для перечислимого типа значение всегда должно означать «все флаги сняты».

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Добавление значения в перечисления

Очень часто обнаруживается, что необходимо добавить значения в перечисление после того, как вы уже отгрузили их. Существует потенциальная проблема совместимости приложений, когда вновь добавленное значение возвращается из существующего API, так как плохо написанные приложения могут неправильно работать с новым значением.

✔️ Рассмотрите возможность добавления значений в перечисления, несмотря на небольшую угрозу совместимости.

Если у вас есть реальные данные о несовместимости приложений, вызванные дополнениями к перечислению, рассмотрите возможность добавления нового API, возвращающего новые и устаревшие значения, и прекращения использования старого API, который должен возвращать только старые значения. Это обеспечит совместимость существующих приложений.

*Части © 2005, 2009 Корпорация Майкрософт. Все права защищены.*

*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*

## <a name="see-also"></a>См. также статью

- [Рекомендации по проектированию типов](type.md)
- [Рекомендации по проектированию платформы](index.md)
