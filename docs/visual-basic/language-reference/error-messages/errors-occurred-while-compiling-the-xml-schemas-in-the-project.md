---
description: 'Дополнительные сведения о: BC36810: ошибка при компиляции XML-схем в проекте'
title: При компиляции XML-схем в проекте возникли ошибки
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 78e88208c0d3df12e7bad8ab46b1d91bce559923
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796487"
---
# <a name="bc36810-errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>BC36810: произошли ошибки при компиляции XML-схем в проекте

Произошли ошибки при компиляции XML-схем в проекте. По этой причине XML IntelliSense недоступен.

 Ошибка в схеме определения схемы XML (XSD), включенной в проект. Эта ошибка возникает при добавлении файла XSD-схемы (XSD), который конфликтует с существующим набором схем XSD для проекта.

 **Идентификатор ошибки:** BC36810

## <a name="to-correct-this-error"></a>Исправление ошибки

- Дважды щелкните предупреждение в окне **Список ошибок** . Visual Basic перейдет к расположению в XSD-файле, который является источником предупреждения. Исправьте ошибку в схеме XSD.

- Убедитесь, что в проект включены все необходимые файлы XSD-схемы (. xsd). Чтобы просмотреть XSD-файлы в **Обозреватель решений**, может потребоваться выбрать пункт **Показать все файлы** в меню **проект** . Щелкните правой кнопкой мыши XSD-файл и выберите **включить в проект** , чтобы включить файл в проект.

- Если используется Мастер XML для схемы, эта ошибка может возникать, если вы выводите схемы несколько раз из одного источника. В этом случае можно удалить существующие файлы XSD-схемы из проекта, добавить новый XML в шаблон элемента схемы, а затем предоставить мастеру XML для схемы все применимые источники XML для вашего проекта.

- Если в схеме XSD не обнаружена ошибка, компилятор XML может не иметь достаточной информации для предоставления подробного сообщения об ошибке. Если вы убедитесь, что пространства имен XML для XSD-файлов, включаемых в проект, соответствуют пространствам имен XML, определенным для набора XML-схем в Visual Studio, вы можете получить более подробные сведения об ошибках.

## <a name="see-also"></a>См. также

- [Окно список ошибок](/visualstudio/ide/reference/error-list-window)
- [XML](../../programming-guide/language-features/xml/index.md)
