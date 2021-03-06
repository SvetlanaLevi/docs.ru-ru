---
title: Практическое руководство. Задание параметров слияния в PLINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 7c7979dc828f89435422b464b22710b3a052911b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722431"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Практическое руководство. Задание параметров слияния в PLINQ

Этот пример демонстрирует, как указать параметры слияния, которые будут применяться ко всем последующим операторам в запросе PLINQ. Параметры слияния не обязательно указывать явным образом, но иногда это может повысить производительность. Дополнительные сведения о параметрах слияния см. в разделе [Параметры слияния в PLINQ](merge-options-in-plinq.md).  
  
> [!WARNING]
> Этот пример предназначен для демонстрации использования и может выполняться не быстрее аналогичного последовательного запроса LINQ to Objects. Дополнительные сведения см. в статье [Общее представление об ускорении выполнения в PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Пример  

 Следующий пример демонстрирует поведение параметров слияния в простом сценарии, в котором ресурсоемкая функция применяется к каждому элементу неупорядоченного источника.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 В случаях, если вариант <xref:System.Linq.ParallelMergeOptions.AutoBuffered> приводит к нежелательной задержке перед получением первого элемента, попробуйте вариант <xref:System.Linq.ParallelMergeOptions.NotBuffered>, чтобы получать результаты быстрее и спокойнее.  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Linq.ParallelMergeOptions>
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
