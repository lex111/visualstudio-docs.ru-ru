---
title: Вкладка "файл страницы", диалоговое окно "Свойства процесса" | Документация Майкрософт
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
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa1eba7af60638d82c791958af6bf66a3272242
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570567"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Вкладка "Файл подкачки" диалогового окна "Свойства процесса"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вкладка "файл страницы", диалоговое окно "Свойства процесса"](https://docs.microsoft.com/visualstudio/debugger/page-file-tab-process-properties-dialog-box).  
  
Используйте **файла подкачки** вкладку, чтобы проанализировать файл подкачки процесса. Для отображения [диалоговое окно "Свойства процесса"](../debugger/process-properties-dialog-box.md), перемещение фокуса к [представление процессов](../debugger/processes-view.md) окна. Выберите любой узел процесса в дереве, а затем выберите **свойства** из **представление** меню.  
  
 Следующие параметры доступны на **файла подкачки** вкладке:  
  
|Ввод|Описание|  
|-----------|-----------------|  
|**Байтов файла подкачки**|Текущее количество страниц, которые использует этот процесс в файле подкачки. Страниц данных, используемой процессом, но не содержится в других файлах хранятся в файл подкачки. Файл подкачки используется всеми процессами и нехватки места в файле подкачки может привести к ошибкам при выполнении других процессов.|  
|**Байтов файла подкачки (пик)**|Максимальное число страниц, использующие этот процесс в файле подкачки.|  
|**Ошибки страниц**|Количество ошибок страниц за потоков, выполняемых в этом процессе. Сбой страницы происходит, когда поток ссылается на страницу виртуальной памяти, который не находится в соответствующем рабочем наборе в основной памяти. Таким образом, страницы не быть получена с диска, если они находятся в списке ожидания и, следовательно, в основной памяти, или если он используется другим обработать с помощью страницы, который является общим.|



