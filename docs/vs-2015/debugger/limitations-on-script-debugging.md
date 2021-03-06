---
title: Ограничения на отладку скриптов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aebdb57d9a242280be82e04c2a550159cba985d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559213"
---
# <a name="limitations-on-script-debugging"></a>Ограничения на отладку скриптов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ограничения на отладку скриптов](https://docs.microsoft.com/visualstudio/debugger/limitations-on-script-debugging).  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] поддерживает отладку клиентского скрипта с некоторыми ограничениями, которые описаны в этом разделе.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Ограничения на сопоставление точки останова с клиентским скриптом  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет установить точку останова в ASPX-файле или HTML-файле на стороне сервера, который преобразуется в файл на стороне клиента во время выполнения. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] сопоставляет точку останова в файле на стороне сервера с соответствующей точкой останова в файле на стороне клиента с учетом следующих ограничений.  
  
-   Точки останова должны быть установлены внутри блоков `<script>`. Невозможно сопоставление точек останова во встроенном скрипте или блоках `<% %>`.  
  
-   URL-адрес браузера для страницы должен содержать имя страницы. Например, http://microsoft.com/default.apsx. Сопоставление точек останова невозможно распознать перенаправление с адреса, такие как http://microsoft.com на страницу по умолчанию.  
  
-   Точка останова должна быть задана на странице, указанной в URL-адресе браузера, а не в файле (ascx) элемента управления ASPX, эталонной странице или другом файле, включенном в эту страницу. Точки останова, установленные во включенных страницах, не могут быть сопоставлены.  
  
-   Невозможно сопоставление точек останова, установленных в блоках `<script defer=true>`.  
  
-   При сопоставлении точек останова, установленных в блоках `<script id="">`, игнорируется атрибут `id`.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Сопоставление точек останова и повторяющиеся строки  
 Производя поиск соответствующего расположения в серверном и клиентском скриптах, алгоритм сопоставления точек останова проверяет каждую строку кода. Каждая строка рассматривается алгоритмом как уникальная. Если несколько (две и больше) строк содержат одинаковый код и точка останова установлена на одной из этих повторяющихся строк, алгоритм сопоставления точек останова может выбрать неверную дублирующую строку в клиентском файле. Во избежание этого к строке, где установлена точка останова, необходимо добавлять комментарий. Пример:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```



