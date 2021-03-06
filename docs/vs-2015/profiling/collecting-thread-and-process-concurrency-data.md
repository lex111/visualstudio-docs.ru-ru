---
title: Сбор данных о параллелизме потоков и процессов | Документы Майкрософт
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
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd63966dba73d57d12d68552e57828b9d17ee84e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592852"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Сбор данных о параллелизме потоков и процессов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [сбор потоков и обработки параллелизма данных](https://docs.microsoft.com/visualstudio/profiling/collecting-thread-and-process-concurrency-data).  
  
Метод профилирования параллелизма средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет собирать данные о конфликтах ресурсов, которые содержат информацию о каждом событии синхронизации, которое принуждает функцию в профилируемом приложении ожидать доступ к ресурсу.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 Метод профилирования параллелизма можно задать с помощью одной из приведенных ниже процедур.  
  
-   На первой странице мастера профилирования щелкните **Параллелизм**.  
  
-   На странице **Общие** диалогового окна свойств сеанса анализа производительности выберите **Параллелизм**.  
  
-   На панели инструментов **обозревателя производительности** в списке **Метод** щелкните пункт **Параллелизм**.  
  
## <a name="common-tasks"></a>Общие задачи  
 Дополнительные параметры можно указать в диалоговом окне _Сеанс производительности_**страницы свойств** сеанса анализа производительности. Чтобы открыть это диалоговое окно, выполните указанные ниже действия.  
  
-   В **обозревателе производительности**щелкните правой кнопкой мыши имя сеанса анализа производительности и выберите пункт **Свойства**.  
  
 В задачах в приведенной ниже таблице описываются параметры, которые можно задать в диалоговом окне _Сеанс производительности_**Страницы свойств** при профилировании с помощью метода параллелизма.  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|На странице **Общие** задайте сведения об имени создаваемого файла данных профилирования (VSP).|-   [Практическое руководство. Настройка параметров имени файла с данными о производительности](../profiling/how-to-set-performance-data-file-name-options.md)|  
|На странице **Запуск** укажите приложение для запуска, если в решении с кодом содержится несколько проектов исполняемых файлов (EXE).|-   [Практическое руководство. Указание двоичного файла для запуска](../profiling/how-to-specify-the-binary-to-start.md)|  
|На странице **Взаимодействие уровней** добавьте данные вызова ADO.NET в сеанс профилировщика.|-   [Сбор данных взаимодействия уровней](../profiling/collecting-tier-interaction-data.md)|  
|На странице **Счетчики Windows** выберите один или несколько счетчиков производительности операционной системы, значения которых будут добавляться в данные профилирования в качестве меток.|-   [Практическое руководство. Сбор данных счетчиков производительности Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|На странице **Дополнительно** укажите версию среды выполнения .NET Framework для профилирования, если модули приложения используют несколько версий. По умолчанию профилируется первая загруженная версия.|-   [Практическое руководство. Определение среды выполнения .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|



