---
description: 'Дополнительные сведения: поставщик отражения (службы данных WCF)'
title: Поставщик отражений (службы данных WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: e09c9a86bb940681d8de24f5082919aea897795d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794927"
---
# <a name="reflection-provider-wcf-data-services"></a>Поставщик отражений (службы данных WCF)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

Помимо предоставления данных из модели данных с помощью Entity Framework службы данных WCF может предоставлять данные, не определенные строго в модели на основе сущностей. Поставщик отражения предоставляет данные в классах, типы возвращаемого значения которых реализуют интерфейс <xref:System.Linq.IQueryable%601>. Службы данных WCF использует отражение для определения модели данных для этих классов и может преобразовывать запросы на основе адресов к ресурсам в запросах на основе LINQ к предоставленным <xref:System.Linq.IQueryable%601> типам.

> [!NOTE]
> Метод <xref:System.Linq.Queryable.AsQueryable%2A> позволяет получить интерфейс <xref:System.Linq.IQueryable%601> любого класса, реализующего интерфейс <xref:System.Collections.Generic.IEnumerable%601>. Это позволяет использовать большинство типов универсальных коллекций в качестве источника данных для службы данных.

Поставщик отражения поддерживает иерархии типов. Дополнительные сведения см. в разделе [инструкции. Создание службы данных с помощью поставщика отражения](create-a-data-service-using-rp-wcf-data-services.md).

## <a name="inferring-the-data-model"></a>Выведение модели данных

При создании службы данных поставщик выводит модель данных при помощи отражения. В следующем списке показано, как поставщик отражения выводит модель данных.

- Контейнер сущностей — класс, предоставляющий данные в виде свойств, возвращаемых экземпляром <xref:System.Linq.IQueryable%601>. При обращении к модели данных на основе отражения контейнер сущностей представляет корневой объект службы. В одном пространстве имен поддерживается только один класс контейнера сущностей.

- Наборы сущностей — свойства, возвращаемые экземплярами <xref:System.Linq.IQueryable%601>, которые рассматриваются как наборы сущностей. Наборы сущностей непосредственно адресуются в запросе как ресурсы. Только одно свойство контейнера сущностей может возвращать экземпляр <xref:System.Linq.IQueryable%601> данного типа.

- Типы сущностей — тип `T` объекта <xref:System.Linq.IQueryable%601>, возвращаемого набором сущностей Классы, являющиеся частью иерархии наследования, преобразуются поставщиком отражения в эквивалентную иерархию типов сущностей.

- Ключи сущностей — каждый класс данных, определяющий тип сущности, должен иметь ключевое свойство. Это свойство помечается с помощью атрибута <xref:System.Data.Services.Common.DataServiceKeyAttribute> (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > Атрибут <xref:System.Data.Services.Common.DataServiceKeyAttribute> следует применять только к сущностям, которые могут быть использованы для уникальной идентификации экземпляра типа сущности. При применении к свойству навигации этот атрибут игнорируется.

- Свойства типов сущностей — помимо ключа сущности, поставщик отражения рассматривает их как доступные свойства (не индексаторы) класса, представляющего тип сущности, следующим образом.

  - Если свойство возвращает примитивный тип, оно рассматривается как свойство типа сущности.

  - Если свойство возвращает тип, который также является типом сущности, то оно рассматривается как свойство навигации, представляющее конец «один» связи «многие к одному» или «один к одному».

  - Если свойство возвращает интерфейс <xref:System.Collections.Generic.IEnumerable%601> типа сущности, оно рассматривается как свойство навигации, представляющее конец «многие» связи «один ко многим» или «многие ко многим».

  - Если тип возвращаемого значения свойства — тип значения, то свойство представляет сложный тип.

> [!NOTE]
> В отличие от модели данных, основанной на реляционной модели сущностей, модели, основанные на поставщике отражения, не поддерживают реляционные данные. Для предоставления реляционных данных через службы данных WCF следует использовать Entity Framework.

## <a name="data-type-mapping"></a>Сопоставление типов данных

Если модель данных выводится из классов .NET Framework, типы-примитивы модели данных сопоставляются с типами данных .NET Framework следующим образом.

|Тип данных платформы .NET|Тип модели данных|
|------------------------------|---------------------|
|<xref:System.Byte> `[]`|`Edm.Binary`|
|<xref:System.Boolean>|`Edm.Boolean`|
|<xref:System.Byte>|`Edm.Byte`|
|<xref:System.DateTime>|`Edm.DateTime`|
|<xref:System.Decimal>|`Edm.Decimal`|
|<xref:System.Double>|`Edm.Double`|
|<xref:System.Guid>|`Edm.Guid`|
|<xref:System.Int16>|`Edm.Int16`|
|<xref:System.Int32>|`Edm.Int32`|
|<xref:System.Int64>|`Edm.Int64`|
|<xref:System.SByte>|`Edm.SByte`|
|<xref:System.Single>|`Edm.Single`|
|<xref:System.String>|`Edm.String`|

> [!NOTE]
> Типы значений платформы .NET Framework, допускающие значения NULL, сопоставляются с теми же типами модели данных, что и соответствующие типы значений, не принимающие значения NULL.

## <a name="enabling-updates-in-the-data-model"></a>Включение обновлений в модели данных

Чтобы разрешить обновление данных, представляемых этим типом модели данных, поставщик отражения определяет интерфейс <xref:System.Data.Services.IUpdatable>. Этот интерфейс описывает метод сохранения обновлений, предоставляемых службой данных типов. Чтобы включить обновление ресурсов, определенных в модели данных, класс контейнера сущностей должен реализовать интерфейс <xref:System.Data.Services.IUpdatable>. Пример реализации <xref:System.Data.Services.IUpdatable> интерфейса см. [в разделе инструкции. Создание службы данных с помощью LINQ to SQL источника данных](create-a-data-service-using-linq-to-sql-wcf.md).

Интерфейс <xref:System.Data.Services.IUpdatable> требует реализации следующих элементов для распространения обновлений источника данных с помощью поставщика отражения.

|Член|Описание|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Предоставляет функциональность добавления объекта в коллекцию связанных объектов, доступ к которым осуществляется через свойство навигации.|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Предоставляет функциональность отмены отложенных изменений данных.|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Предоставляет функциональность создания нового ресурса в указанном контейнере.|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Предоставляет функциональность удаления ресурса.|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Предоставляет функциональность извлечения ресурса, идентифицированного указанным запросом и именем типа.|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Предоставляет функциональность возврата значения свойства ресурса.|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Предоставляет функциональность удаления объекта из коллекции связанных объектов, доступ к которым осуществляется через свойство навигации.|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Предоставляет функциональность обновления указанного ресурса.|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Предоставляет функциональность возврата ресурса, представленного экземпляром определенного объекта.|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Предоставляет функциональность сохранения всех отложенных изменений.|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Предоставляет функциональность задания ссылки на связанный объект с помощью свойства навигации.|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Предоставляет функциональность задания значения свойства ресурса.|

## <a name="handling-concurrency"></a>Обработка параллелизма

Службы данных WCF поддерживает модель оптимистичного параллелизма, позволяя определить маркер параллелизма для сущности. Этот маркер параллелизма, включающий одно или несколько свойств сущности, используется службой данных для определения, произошло ли изменение в запрашиваемых, обновляемых или удаляемых данных. Когда значения маркера, полученные из eTag в запросе, отличаются от текущих значений сущности, служба данных вызывает исключение. <xref:System.Data.Services.ETagAttribute> применяется к типу сущности для определения маркера параллелизма в поставщике отражения. Маркер параллелизма не может содержать ключевое свойство или свойство навигации. Дополнительные сведения см. [в разделе Обновление службы данных](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Использование запросов LINQ к SQL с помощью поставщика отражения

Поскольку Entity Framework изначально поддерживается по умолчанию, это рекомендуемый поставщик данных для использования реляционных данных с службы данных WCF. Однако для работы с запросами LINQ к классам SQL можно использовать и поставщик отражения. <xref:System.Data.Linq.Table%601>Результирующие наборы, возвращаемые методами, <xref:System.Data.Linq.DataContext> созданными реляционный конструктор объектов LINQ to SQL (конструктор O/R), реализуют <xref:System.Linq.IQueryable%601> интерфейс. Это позволяет поставщику отражения получать доступ к таким методам и возвращать данные сущностей с сервера SQL Server при помощи сформированных классов LINQ to SQL. Однако, поскольку запрос LINQ to SQL не реализует интерфейс <xref:System.Data.Services.IUpdatable>, необходимо добавить разделяемый класс, расширяющий имеющийся разделяемый класс <xref:System.Data.Linq.DataContext> и определяющий реализацию интерфейса <xref:System.Data.Services.IUpdatable>. Дополнительные сведения см. в разделе [инструкции. Создание службы данных с помощью LINQ to SQL источника данных](create-a-data-service-using-linq-to-sql-wcf.md).

## <a name="see-also"></a>См. также

- [Поставщики служб данных](data-services-providers-wcf-data-services.md)
