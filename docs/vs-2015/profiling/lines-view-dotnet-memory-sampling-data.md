---
title: Представление "Строки" — данные выборки памяти .NET | Документы Майкрософт
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
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3aa0c91cb6f26dd2a914195791c12421798c43b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559647"
---
# <a name="lines-view---net-memory-sampling-data"></a>Представление "Строки" — данные выборки памяти .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [представление "строки" — данные выборки памяти .NET](https://docs.microsoft.com/visualstudio/profiling/lines-view-dotnet-memory-sampling-data).  
  
В представлении "Строки" данных профилирования выделения памяти .NET, собранных методом выборки, перечислены операторы, которые выделяли память в сеансе профилирования. Столбцы также показывают размер и число выделений.  
  
 В исходном файле инструкция может занимать несколько строк, а одна строка может включать несколько инструкций.  
  
 Оператор определяется следующими данными:  
  
-   исходным файлом, который содержит оператор функции;  
  
-   функцией, содержащей оператор;  
  
-   исходной строкой, с которой начинается оператор;  
  
-   знаком исходной строки, с которой начинается оператор;  
  
-   исходной строкой, которой заканчивается оператор;  
  
-   знаком исходной строки, которой заканчивается оператор.  
  
 Столбец "Имя строки" содержит объединение идентификаторов и поддерживает сортировку.  
  
 По определению оператор не вызывает другие функции. Поэтому перечисляются только эксклюзивные значения.  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Идентификатор процесса**|Идентификатор процесса (PID) сеанса профилирования.|  
|**Имя процесса**|Имя процесса.|  
|**Имя модуля**|Имя модуля, содержащего оператор.|  
|**Путь к модулю**|Путь к модулю, содержащему оператор.|  
|**Исходный файл**|Исходный файл, содержащий оператор.|  
|**Имя функции**|Имя функции, содержащей оператор.|  
|**Номер строки функции**|Номер строки, на которой эта функция начинается в исходном файле.|  
|**Адрес функции**|Начальный адрес функции.|  
|**Начало исходной строки**|Начальный номер строки исходного файла, в котором произошла операция выделения.|  
|**Конец исходной строки**|Конечный номер строки исходного файла, в котором произошла операция выделения.|  
|**Начало исходного символа**|Смещение начального символа в строке исходного файла, в котором произошла операция выделения.|  
|**Конец исходного символа**|Смещение конечного символа в строке исходного файла, в котором произошла операция выделения.|  
|**Имя строки**|Созданный профилировщиком идентификатор строки со следующим синтаксисом:`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number Start,Character Start`**]**|  
|**Исключающие выделения**|Общее число объектов, которые были созданы в этой строке.|  
|**% эксклюзивных выделений**|Процент от общего числа объектов, созданных в ходе сеанса профилирования, которые были выделены в этой строке.|  
|**Эксклюзивные байты**|Процент от общего числа байтов памяти, выделенных в ходе сеанса профилирования, которые были выделены в этой строке.|  
|**% эксклюзивных байтов**|Процент от общего числа байтов памяти, выделенных в ходе сеанса профилирования, которые были выделены в этой строке.|  
  
## <a name="see-also"></a>См. также  
 [Представление "Строки"](../profiling/lines-view-sampling-data.md)



