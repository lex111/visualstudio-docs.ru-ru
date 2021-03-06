---
title: 'Практическое: поиск имени процесса ASP.NET | Документация Майкрософт'
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d29d40f55bc693040d1acce632feba72b0a58d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561192"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Практическое руководство. Поиск имени процесса ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: поиск имени процесса ASP.NET](https://docs.microsoft.com/visualstudio/debugger/how-to-find-the-name-of-the-aspnet-process).  
  
Чтобы выполнить присоединение к выполняющемуся приложению [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], необходимо знать имя процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
-   Если выполняется IIS 6.0 или IIS 7.0, процесс имеет имя w3wp.exe.  
  
-   Если выполняется более ранняя версия IIS, то процесс имеет имя aspnet_wp.exe.  
  
 Для приложений, созданных с помощью [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] или более поздних версиях [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] код может находиться в файловой системе и выполняться под управлением тестового сервера WebDev.WebServer.exe. В этом случае необходимо выполнить присоединение к WebDev.WebServer.exe вместо присоединения к процессу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Этот скрипт применим только к локальной отладке.  
  
 Более ранние версии приложений ASP при внутрипроцессном выполнении выполняются в процессе inetinfo.exe.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Определение, размещен ли код проекта в файловой системе или IIS  
  
1.  В Visual Studio откройте **обозревателе решений** если он еще не открыт.  
  
2.  Выберите узел верхнего уровня, который содержит имя приложения.  
  
3.  Если **свойства** заголовок окна содержит путь к файлу, код приложения расположен в файловой системе.  
  
     В противном случае **свойства** заголовок окна будет содержать имя веб-сайта.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Определение версии IIS, в которой выполняется приложение  
  
1.  Найти **Администрирование** и запустите его. В зависимости от используемой операционной системой, это может быть значка в **панели управления**, или в меню, открываемом кнопкой **запустить**.  
  
     В Windows XP **панели управления** может находиться в представлении по категориям или классический вид. В представлении по категориям, вам придется щелкнуть **переключение к классическому виду** или **производительность и обслуживание** для см. в разделе **Администрирование** значок.  
  
2.  Из **Администрирование**, запустите службы IIS. Появится диалоговое окно MMC.  
  
3.  Если в левой области перечислены несколько компьютеров, выберите тот из них, на котором расположен код приложения.  
  
4.  Версия IIS, **версии** столбец в правой области.  
  
## <a name="see-also"></a>См. также  
 [Условия для удаленной отладки веб-приложений](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Требования к системе для .NET Framework](../debugger/aspnet-debugging-system-requirements.md)   
 [Подготовка к отладке ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Отладка веб-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)



