---
title: 'DA0026: обработка чрезмерного времени ядра ЦП | Документы Майкрософт'
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
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29eda10403e2d09f5a1bdf67911e1f2ae58bd9f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561469"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: обработка чрезмерного времени ядра ЦП
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DA0026: обработка чрезмерного ядра ЦП время](https://docs.microsoft.com/visualstudio/profiling/da0026-excessive-kernel-cpu-time-processing).  
  
ИД правила | TODO |  
| Категория | Использование средств профилирования |  
| Метод профилирования | Выборка |  
| Сообщение | Измерялась относительно большое количество времени ЦП в режиме ядра. Рассмотрите возможность выявления источника выборку по SysCall. |  
| Тип правила | Сведения |  
  
 При профилировании с помощью выборки, памяти .NET или методов разрешения конфликтов ресурсов необходимо собрать минимум 10 выборок, чтобы активировать это правило.  
  
## <a name="cause"></a>Причина  
 Доля времени ЦП в режиме ядра превысила время, затраченное в пользовательском режиме. Рекомендуется повторить профилирование и сделать выборку по числу системных вызовов (syscall), чтобы определить причину высокой доли времени выполнения в режиме ядра.  
  
## <a name="rule-description"></a>Описание правила  
 Относительно большая доля времени, затраченного приложением на выполнение в режиме ядра, может потребовать дальнейшего изучения. Приложение пользовательского режима переходит в режим ядра для выполнения операций ввода-вывода, ожидания примитивов синхронизации потоков или процессов либо выполнения системных вызовов. Можно изучить характер системных вызовов приложения и определить функции, которые отвечают за них, если выбран параметр для сбора выборок стеков вызова на основе системных вызовов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы изучить характер системных вызовов приложения, запустите профилирование повторно и выберите параметр для сбора выборок на основе системных вызовов. Для получения дополнительных сведений см. раздел [Практическое руководство. Выбор событий выборки](../profiling/how-to-choose-sampling-events.md), если вы выполняете средства профилирования в интегрированной среде разработки. Если средства профилирования выполняются из командной строки, см. раздел **Параметры интервала выборки** статьи [VSPerfCmd](../profiling/vsperfcmd.md) справочника по средствам командной строки средств профилирования.



