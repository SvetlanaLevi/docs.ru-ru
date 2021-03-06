---
description: Дополнительные сведения о сопоставлении типов данных в ADO.NET
title: Сопоставления типов данных
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: c1829fdc2ebc053d1fd3a76e827a81e582572233
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786450"
---
# <a name="data-type-mappings-in-adonet"></a>Сопоставления типов данных в ADO.NET

Платформа .NET Framework основана на общей системе типов, в которой определяются способы объявления, использования типов и управления ими во время выполнения. Система типов состоит из типов-значений и типов-ссылок, производных от базового типа <xref:System.Object>. При работе с источником данных не указанный явным образом тип данных выводится из поставщика данных. Например, объект <xref:System.Data.DataSet> не зависит ни от одного конкретного источника данных. Получение данных в `DataSet` осуществляется из источника данных, а изменения передаются для сохранения в источнике данных с использованием `DataAdapter`. Это означает, что при `DataAdapter` заполнении <xref:System.Data.DataTable> в `DataSet` со значениями из источника данных результирующие типы данных столбцов в `DataTable` являются платформа .NET Framework типами, а не типами, характерными для платформа .NET Frameworkного поставщика данных, используемого для подключения к источнику данных.  
  
 Аналогично, когда `DataReader` возвращает значение из источника данных, результирующее значение сохраняется в локальной переменной с типом .NET Framework. Как для операций, так `Fill` `DataAdapter` и для `Get` методов `DataReader` , тип платформа .NET Framework выводится из значения, возвращаемого поставщиком данных платформа .NET Framework.  
  
 Если известен тип возвращаемого значения, то вместо выводимого типа данных можно воспользоваться типизированными методами доступа объекта `DataReader`. Типизированные методы доступа обеспечивают оптимальную производительность, возвращая значение с конкретным типом .NET Framework, что устраняет необходимость в дополнительном преобразовании типов.  
  
> [!NOTE]
> Значения NULL для типов данных поставщика данных платформа .NET Framework представлены в `DBNull.Value` .  
  
## <a name="in-this-section"></a>В этом разделе  

 [Сопоставления типов данных SQL Server](sql-server-data-type-mappings.md)  
 Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.SqlClient>.  
  
 [Сопоставления типов данных OLE DB](ole-db-data-type-mappings.md)  
 Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.OleDb>.  
  
 [Сопоставления типов данных ODBC](odbc-data-type-mappings.md)  
 Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.Odbc>.  
  
 [Сопоставления типов данных Oracle](oracle-data-type-mappings.md)  
 Выводит список сопоставлений выводимых типов данных и методов доступа к данным для объекта <xref:System.Data.OracleClient>.  
  
 [Числа с плавающей запятой](floating-point-numbers.md)  
 Описывает проблемы, с которыми разработчики часто сталкиваются при работе с числами с плавающей запятой.  
  
## <a name="see-also"></a>См. также

- [Типы данных SQL Server и ADO.NET](./sql/sql-server-data-types.md)
- [Настройка параметров и типы данных параметров](configuring-parameters-and-parameter-data-types.md)
- [Извлечение сведений о схеме базы данных](retrieving-database-schema-information.md)
- [Система общих типов CTS](../../../standard/base-types/common-type-system.md)
- [Преобразование типов](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [Общие сведения об ADO.NET](ado-net-overview.md)
