---
description: 'Дополнительные сведения: 116-Воркфловинстанцесуспендедрекордвисид'
title: 116 ― WorkflowInstanceSuspendedRecord
ms.date: 03/30/2017
ms.assetid: 38232c03-6139-4494-a020-79bc83eb9dce
ms.openlocfilehash: 32746777d32ed0c8320d53da9f73ddb8d55a5573
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703254"
---
# <a name="116---workflowinstancesuspendedrecordwithid"></a>116 ― WorkflowInstanceSuspendedRecord

## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|ID|116|  
|Keywords|HealthMonitoring, WFTracking|  
|Уровень|Сведения|  
|Канал|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Описание  

 Это событие создается участником отслеживания ETW, когда экземпляр рабочего процесса создает запись WorkflowInstanceSuspendedRecord.  
  
## <a name="message"></a>Сообщение  

 TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8  
  
## <a name="details"></a>Сведения  
  
|Имя элемента данных|Тип элемента данных|Описание|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Идентификатор экземпляра для рабочего процесса.|  
|RecordNumber|xs:long|Порядковый номер созданной записи.|  
|EventTime|xs:dateTime|Время в формате UTC, когда было создано событие.|  
|ActivityDefinitionId|xs:string|Имя корневого действия в рабочем процессе.|  
|Область|xs:string|Текущее состояние рабочего процесса.|  
|Заметки|xs:string|Заметки, добавленные к этому событию. Значения хранятся в XML-элементе в формате \<items> \< item name = "annotationName" type="System.String"> аннотатионвалуе \</item> \</items> . Если заметки не указаны, строка содержит \<items/> . Размер событий ETW ограничен размером буфера ETW или максимальным размером полезных данных для события ETW. Если размер события превышает предел ETW, то событие усекается путем удаления заметок и замены значения аннотации на \<items> ... \</items> .|  
|ProfileName|xs:string|Имя или профиль отслеживания, который привел к созданию этого события.|  
|WorkflowDefinitionIdentity|xs:string|Идентификатор определения рабочего процесса|  
|Домен приложения|xs:string|Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.|
