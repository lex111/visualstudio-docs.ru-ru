---
title: Настройка сеансов анализа производительности | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e804e1638574d6918a1db4effbfbc1c20c80f63e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562076"
---
# <a name="configuring-performance-sessions"></a>Настройка сеансов анализа производительности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Настройка сеансов анализа производительности](https://docs.microsoft.com/visualstudio/profiling/configuring-performance-sessions).  
  
Средства профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяют собирать большой объем данных о производительности для приложений различных типов. В данном разделе описывается, как использовать мастер производительности и свойства сеанса анализа производительности и целевого двоичного файла для настройки средств профилирования для сбора интересующих вас данных. Свойства конфигурации средств профилирования могут также использоваться для управления объемом данных, собираемых в ходе сеанса профилирования. Дополнительные сведения см. в статье [Controlling Data Collection](../profiling/controlling-data-collection.md) (Управление сбором данных).  
  
> [!NOTE]
>  Во многих случаях использование свойств по умолчанию мастера производительности обеспечивает эффективный сбор данных профилирования. Дополнительные сведения см. в статьях [Beginners Guide to Performance Profiling](../profiling/beginners-guide-to-performance-profiling.md) (Руководство по профилированию производительности для начинающих) и [Начало работы](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Настройка базовых параметров профилирования.** Следует настроить [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] для использования сервера символов Майкрософт. Это обеспечивает доступ к символам, таким как имена функций и параметров, для текущей версии Windows и других приложений Майкрософт. Можно также указать другие общие параметры до начала сеанса профилирования, например системные разрешения для средств профилирования и имена файлов данных профилирования.|-   [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Практическое руководство. Сериализация сведений о символах](../profiling/how-to-serialize-symbol-information.md)<br />-   [Практическое руководство. Установка текущего сеанса](../profiling/how-to-set-the-current-session.md)<br />-   [Практическое руководство. Установка разрешений](../profiling/how-to-set-permissions.md)<br />-   [Практическое руководство. Настройка параметров имени файла с данными о производительности](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Определение собираемых данных.** Процедуры, которые используются для настройки сеанса профилирования, зависят от типа целевого профилируемого приложения и типа собираемых данных производительности.|-   [Практическое руководство. Выбор методов сбора данных](../profiling/how-to-choose-collection-methods.md)<br />-   [Использование метода выборки для сбора статистики производительности](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Сбор данных о выделении памяти для объектов .NET и времени их жизни](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Практическое руководство. Профилирование кода JavaScript в веб-страницах](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Сбор данных о параллелизме потоков и процессов](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Сбор дополнительных данных о производительности](../profiling/collecting-additional-performance-data.md)|  
|**Настройка расширенных параметров конфигурации.** Во время профилирования приложений .NET Framework, которые загружают несколько версий CLR, можно указать профилируемую версию. Если в сеансе анализа производительности используется несколько EXE-файлов, можно настроить порядок запуска двоичных файлов.|-   [Практическое руководство. Определение среды выполнения .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Практическое руководство. Указание двоичного файла для запуска](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Связанные разделы  
 [Управление сбором данных](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>См. также  
 [Обозреватель производительности](../profiling/performance-explorer.md)



