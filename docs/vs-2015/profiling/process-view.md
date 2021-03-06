---
title: Представление "Процесс" | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6d0c560cdd40651763837bba4e87372eba76007
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562206"
---
# <a name="process-view"></a>Представление "Процесс"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [представление "процесс"](https://docs.microsoft.com/visualstudio/profiling/process-view).  
  
В представлении процесса отображаются данные о профилировании для процессов и потоков, которые выполнялись во время сеанса профилирования.  
  
 Процессы упорядочены по имени. Потоки указываются как дочерние узлы создавших их процессов. Потоки именуются по запустивших их функциям или по метке **[ntdll.dll]** при отсутствии доступных символов.  
  
 Чтобы добавить или удалить столбцы, щелкните правой кнопкой мыши в представлении и выберите **Добавить или удалить столбцы**. Кроме того, щелкнув имя столбца, можно сортировать данные. Дополнительные сведения см. в статье [How to: Customize Report View Columns](../profiling/how-to-customize-report-view-columns.md) (Практическое руководство. Настройка столбцов представлений отчета).  
  
 Столбцы в представлении процесса являются одинаковыми для данных, которые созданы с помощью методов выборки и инструментирования, а также для данных, которые включают данные памяти .NET. В следующей таблице описаны значения столбцов.  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Уникальный идентификатор**|Созданный профилировщиком идентификатор, уникальным образом определяющий процесс или поток.|  
|**Идентификатор**|Созданный системой идентификатор процесса или потока.|  
|**Name**|Имя процесса или потока.|  
|**Время начала**|Количество миллисекунд или циклов процессора от начала профилирования до запуска процесса или потока.|  
|**Время окончания**|Количество миллисекунд или циклов процессора от начала профилирования до завершения процесса или потока.|  
  
## <a name="see-also"></a>См. также  
 [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)   
 [Представления данных метода инструментирования](../profiling/instrumentation-method-data-views.md)   
 [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)



