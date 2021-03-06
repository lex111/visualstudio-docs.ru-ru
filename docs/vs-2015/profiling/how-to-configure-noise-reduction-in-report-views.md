---
title: Практическое руководство. Настройка подавления шума для представлений отчетов | Документы Майкрософт
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
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee848f506a81b156309fa7e0d86891418251d0e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573414"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Практическое руководство. Настройка подавления шума для представлений отчетов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Настройка подавления шума в представлениях отчетов](https://docs.microsoft.com/visualstudio/profiling/how-to-configure-noise-reduction-in-report-views).  
  
В отчетах о производительности можно настроить снижение шума, ограничив количество данных, выводимых в представлениях дерева вызовов и выделений. При использовании функции подавления шума проблемы производительности становятся более наглядными. Это удобно при анализе отчетов о производительности.  
  
 Параметры конфигурации для снижения шума включают следующие.  
  
-   **Обрезка**. При анализе отчета из представления исключаются функции, которые соответствуют настроенным параметрам значения и порогового значения, как описано в процедуре ниже. По умолчанию обрезка включена.  
  
-   **Свертывание**. При включении свертывания последовательные функции в пути, соответствующие настроенным параметрам, будут объединены, как описано в процедуре ниже. По умолчанию свертывание включено.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Настройка обрезки для отчета о производительности  
  
1.  Открыв представление дерева вызовов или выделения в созданном отчете, в меню **Разработчик** щелкните **Профилировщик**, а затем **Параметры снижения шума**.  
  
     Откроется диалоговое окно **Снижение шума**.  
  
2.  Для включения обрезки выполните следующие действия.  
  
    1.  Выберите **Включить обрезку**. Этот параметр используется по умолчанию.  
  
        > [!NOTE]
        >  Если снижение шума включено, в отчете будет отображаться информационная панель. Дополнительные сведения см. в статьях [Представление "Дерево вызовов"](../profiling/call-tree-view.md) и [Представление "Выделения"](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Настройте значение параметра с помощью раскрывающегося списка **Значение**, выбрав соответствующий параметр.  
  
    3.  Настройте нужное пороговое значение. Для этого в текстовом поле **Пороговое значение** введите значение в процентах.  
  
    4.  Чтобы включить предупреждения о снижении шума в созданном отчете, выберите **Отображать предупреждение при включении снижения шума**. Этот параметр используется по умолчанию.  
  
3.  Чтобы отключить обрезку, снимите флажок **Включить обрезку**.  
  
4.  Нажмите кнопку **ОК**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Настройка свертывания для отчета о производительности  
  
1.  В меню **Разработчик** щелкните **Профилировщик**, а затем **Параметры снижения шума**.  
  
     Откроется диалоговое окно **Снижение шума**.  
  
2.  Для включения свертывания выполните следующие действия.  
  
    1.  Выберите **Включить свертывание**. Этот параметр используется по умолчанию.  
  
        > [!NOTE]
        >  Если снижение шума включено, в отчете будет отображаться информационная панель. Дополнительные сведения см. в статьях [Представление "Дерево вызовов"](../profiling/call-tree-view.md) и [Представление "Выделения"](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Настройте значение параметра с помощью раскрывающегося списка **Значение**, выбрав соответствующий параметр.  
  
    3.  Настройте нужное пороговое значение. Для этого в текстовом поле **Пороговое значение** введите значение в процентах.  
  
    4.  Чтобы включить предупреждения о снижении шума в созданном отчете, выберите **Отображать предупреждение при включении снижения шума**. Этот параметр используется по умолчанию.  
  
3.  Чтобы отключить свертывание, снимите флажок **Включить свертывание**.  
  
4.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Настройка представлений отчетов средств производительности](../profiling/customizing-performance-tools-report-views.md)   
 [Практическое руководство. Исключение и включение малых функций при инструментировании](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Представление "Дерево вызовов"](../profiling/call-tree-view.md)   
 [Представление "Выделения"](../profiling/dotnet-memory-allocations-view.md)



