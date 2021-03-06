---
title: Считывание объявлений сущностей и ссылок на сущности в DOM
ms.date: 03/30/2017
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: 8af9e4c1aedc588bcbf3b4f43e9e562fda2f3ce3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686830"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Считывание объявлений сущностей и ссылок на сущности в DOM

Сущность является декларацией, определяющей имя, которое будет использоваться в XML-документе вместо содержимого или разметки. Сущность состоит из двух частей. Во-первых, в декларации сущности необходимо связать имя с заменяющим его содержимым. Декларация сущности создается с помощью синтаксиса `<!ENTITY name "value">` определения DTD или схемы XML. Во-вторых, определенное в декларации сущности имя впоследствии используется в XML-документе. При использовании в XML-документе оно называется ссылкой на сущность. Например, следующая декларация сущности определяет сущность с именем `publisher`, связанную с содержимым «Microsoft Press».  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 В следующем примере показано использование декларации сущности в XML в качестве ссылки на сущность.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Некоторые средства синтаксического анализа автоматически развертывают сущности при загрузке документа в память. Поэтому, когда XML-документ считывается в память, декларации сущностей запоминаются и сохраняются. Если средство синтаксического анализа впоследствии встречает символы `&;`, определяющие ссылку на общую сущность, оно ищет это имя в таблице деклараций сущностей. Ссылка `&publisher;` заменяется содержимым, которое она представляет. Используя следующий XML-код,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 разворачивает ссылку на сущность и заменяет `&publisher;` содержимым Microsoft Press, формируя следующий расширенный XML.  
  
 **Выходные данные**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Существует много типов сущностей. На следующей схеме показана классификация типов сущности и терминология.  
  
 ![Блок-схема иерархии типов сущностей](media/entity-hierarchy.gif "Entity_hierarchy")  
  
 По умолчанию реализация модели DOM на платформе Microsoft .NET Framework сохраняет ссылки на сущности и не развертывает их при загрузке XML. Это означает, что при загрузке документа в модель DOM создается узел **XmlEntityReference`&publisher;`, содержащий ссылочную переменную** , с дочерними узлами, представляющими содержимое сущности, объявленной в определении DTD.  
  
 Следующая схема на примере объявления сущности `<!ENTITY publisher "Microsoft Press">` демонстрирует узлы **XmlEntity** и **XmlText**, создаваемые на основе этого объявления.  
  
 ![Узлы, созданные на основе объявления сущностей](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Будут ли развертываться ссылки на сущности или нет - зависит от вида узлов, создаваемых в дереве модели DOM в памяти. Различия между созданными узлами объясняется в статьях [Сохраняемые ссылки на сущности](entity-references-are-preserved.md) и [Разворачиваемые и не сохраняемые ссылки на сущности](entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>См. также

- [Модель объектов документов XML (DOM)](xml-document-object-model-dom.md)
