---
description: 'Дополнительные сведения о: неправильное имя файла или номер'
title: Недопустимое имя файла или номер
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 6e568a721fb3606c5b4bc046041c9d6f24b6d126
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797072"
---
# <a name="bad-file-name-or-number"></a>Недопустимое имя файла или номер

Произошла ошибка при попытке доступа к указанному файлу. Среди возможных причин этой ошибки:  
  
- Оператор ссылается на файл с именем или номером файла, который не был указан в `FileOpen` инструкции или был указан в `FileOpen` инструкции, но впоследствии был закрыт.  
  
- Оператор ссылается на файл с номером, который выходит за пределы диапазона номеров файлов.  
  
- Оператор ссылается на недопустимое имя файла или номер.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Убедитесь, что имя файла указано в `FileOpen` инструкции. Обратите внимание, что при вызове `FileClose` инструкции без аргументов вы могли случайно закрыть все открытые файлы.  
  
2. Если код создает номера файлов алгоритмически, убедитесь, что числа допустимы.  
  
3. Проверьте имена файлов, чтобы убедиться, что они соответствуют соглашениям об операционной системе.  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Соглашения об именах Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
