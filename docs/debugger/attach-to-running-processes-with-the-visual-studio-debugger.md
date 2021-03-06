---
title: Присоединение к выполняемым процессам с отладчиком в Visual Studio | Документация Майкрософт
ms.custom: H1Hack27Feb2017
ms.date: 06/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc638bdd70e9456ea1f2c937febbfdd974f2d20
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443640"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Присоединение к выполняемым процессам с использованием отладчика Visual Studio
Отладчик Visual Studio можно подключить к запущенному процессу на локальном или удаленном компьютере. Запустив процесс, выберите **Отладка** > **присоединение к процессу** или нажмите клавишу **Ctrl**+**Alt** + **P** в Visual Studio и использовать **присоединение к процессу** диалоговое окно, чтобы подключить отладчик к процессу.

Можно использовать **присоединение к процессу** для отладки запущенного приложения на локальном или удаленных компьютерах, одновременной отладки нескольких процессов, отладки приложений, которые не были созданы в Visual Studio или отладке любого приложения, вы не запускали из Visual Studio с подключен отладчик. Например если вы запускаете приложение без отладчика и исключение, можно затем подключить отладчик к процессу, запустив его и начните отладку.

Сведения о основы отладки в Visual Studio, см. в разделе [Приступая к работе с отладчиком](../debugger/getting-started-with-the-debugger.md).

> [!TIP]
> Не уверены, следует ли использовать **присоединение к процессу** для отладки сценария? См. в разделе [распространенных сценариях отладки](#BKMK_Scenarios). 

##  <a name="BKMK_Attach_to_a_running_process"></a> Присоединение к выполняющемуся процессу на локальном компьютере  

Чтобы быстро повторно подключиться к процессу, к которым ранее ранее, см. в разделе [повторно подключиться к процессу](#BKMK_reattach). 

Для отладки процесса на удаленном компьютере, см. в разделе [присоединение к процессу на удаленном компьютере](#BKMK_Attach_to_a_process_on_a_remote_computer).

**Для присоединения к процессу на локальном компьютере:**  

1.  В Visual Studio выберите **Отладка** > **присоединение к процессу** (или нажмите клавишу **Ctrl**+**Alt** + **P**) чтобы открыть **присоединение к процессу** диалоговое окно.
  
  **Тип соединения** должно быть присвоено **по умолчанию**. **Цель подключения** должно быть имя вашего локального компьютера. 
  
  ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
1.  В **доступные процессы** списке найдите и выберите процесса или процессов, которые вы хотите присоединить.  

  - Чтобы быстро выбрать процесс, введите его имя или первую букву в **процессы фильтрации** поле. 
  
  - Если вы не знаете имя процесса, найти его в списке, или см. в разделе [распространенных сценариях отладки](#BKMK_Scenarios) для некоторых распространенных имена процессов. 
  
  >[!TIP]
  >Процессы можно запускать и останавливать в фоновом режиме при **присоединение к процессу** диалоговое окно открыт, поэтому список выполняющихся процессов может не всегда быть текущей. Можно выбрать **обновить** в любое время, чтобы просмотреть текущий список. 
  
1.  В **присоединить к** поле, убедитесь, что указан тип кода, которые планируется отлаживать. Значение по умолчанию **автоматического** задание работает для большинства типов приложений. 
  
  Чтобы вручную выбрать типы кода:
    1. Нажмите кнопку **Выбрать**. 
    1. В **Выбор типа кода** диалоговом окне выберите **отладить код следующих типов**.
    1. Выберите типы кода, которые необходимо выполнить отладку.
    1. Нажмите кнопку **ОК**.
  
1.  Выберите **присоединить**.
  
>[!NOTE]
>Можно подключиться к нескольким приложениям для отладки, но только одно приложение активна в отладчике одновременно. Можно задать активного приложения в Visual Studio **место отладки** панели инструментов или **процессы** окна.  

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Присоединение к процессу на удаленном компьютере  

Можно также выбрать удаленный компьютер в **присоединение к процессу** диалоговое окно, просмотреть список доступных процессов, запущенных на этом компьютере и подключить к одному или нескольким процессам для отладки. Удаленный отладчик (*msvsmon.exe*) должна быть запущена на удаленном компьютере. Дополнительные сведения см. в разделе [удаленной отладки](../debugger/remote-debugging.md). 

Более подробные инструкции для отладки приложений ASP.NET, которые были развернуты в IIS см. в разделе [удаленная отладка ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Для присоединения к выполняющемуся процессу на удаленном компьютере:**  

1.  В Visual Studio выберите **Отладка** > **присоединение к процессу** (или нажмите клавишу **Ctrl**+**Alt** + **P**) чтобы открыть **присоединение к процессу** диалоговое окно.
  
1.  **Тип соединения** должно быть **по умолчанию** для большинства случаев. В **цель подключения** окне выбрать удаленный компьютер, с помощью одного из следующих методов:

  - Щелкните стрелку раскрывающегося списка рядом с полем **цель подключения**и выберите из раскрывающегося списка имя компьютера.  
  - Введите имя компьютера в **цель подключения** поле.
      
      > [!NOTE]
      > Если не удается подключиться, используя имя удаленного компьютера, попробуйте использовать IP-адрес и порт адрес (например, `123.45.678.9:4022`). 4022 является портом по умолчанию для удаленного отладчика Visual Studio 2017 x64. Другие назначения портов удаленного отладчика, см. в разделе [назначение портов удаленного отладчика](remote-debugger-port-assignments.md).  
      
  - Выберите **найти** рядом с пунктом **цель подключения** окно, чтобы открыть **удаленные подключения** диалоговое окно. **Удаленные подключения** диалоговое окно перечислены все устройства, которые находятся в локальной подсети или непосредственно подключенные к компьютеру. Может потребоваться [откройте порт UDP 3702](../debugger/remote-debugger-port-assignments.md) на сервере для обнаружения удаленных устройств. Выберите компьютер или устройство и нажмите кнопку **выберите**. 
  
  > [!NOTE]
  > **Тип подключения** хранится между сеансами отладки. **Цель подключения** хранится между сеансами отладки только в том случае, если произошла успешного подключения отладки с этой целью.

1.  Нажмите кнопку **обновить** для заполнения **доступные процессы** списка.
     
     >[!TIP]
     >Процессы можно запускать и останавливать в фоновом режиме при **присоединение к процессу** диалоговое окно открыт, поэтому список выполняющихся процессов может не всегда быть текущей. Можно выбрать **обновить** в любое время, чтобы просмотреть текущий список. 
     
1.  В **доступные процессы** списке найдите и выберите процесса или процессов, которые вы хотите присоединить.  

  - Чтобы быстро выбрать процесс, введите его имя или первую букву в **процессы фильтрации** поле. 
  
  - Если вы не знаете имя процесса, найти его в списке, или см. в разделе [распространенных сценариях отладки](#BKMK_Scenarios) для некоторых распространенных имена процессов. 
  
  - Чтобы найти процессы, запущенные все учетные записи пользователей, выберите **Показать процессы всех пользователей** "флажок".
      
      >[!NOTE]
      >Если попытаться подключиться к процессу, работающему под управлением ненадежной учетной записи, появится диалоговое окно подтверждения с предупреждением безопасности. Дополнительные сведения см. в разделе [предупреждение системы безопасности: присоединение к процессу, принадлежит недоверенному пользователю не может быть опасно. Если вы не уверены, ниже сведения, не присоединяться к процессу](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
      
1.  В **присоединить к** поле, убедитесь, что указан тип кода, которые планируется отлаживать. Значение по умолчанию **автоматического** задание работает для большинства типов приложений. 
  
  Чтобы вручную выбрать типы кода:
    1. Нажмите кнопку **Выбрать**. 
    1. В **Выбор типа кода** диалоговом окне выберите **отладить код следующих типов**.
    1. Выберите типы кода, которые необходимо выполнить отладку.
    1. Нажмите кнопку **ОК**.
  
1.  Выберите **присоединить**.
  
>[!NOTE]
>Можно подключиться к нескольким приложениям для отладки, но только одно приложение активна в отладчике одновременно. Можно задать активного приложения в Visual Studio **место отладки** панели инструментов или **процессы** окна.  

В некоторых случаях при отладке в сеансе удаленного рабочего стола (службы терминалов) **доступные процессы** списке не будут отображаться все доступные процессы. Если вы используете Visual Studio в качестве пользователя, имеющего учетную запись пользователя с ограниченными правами **доступные процессы** список не будет отображать процессы, запущенные в сеансе 0, который используется для служб и других серверных процессов, включая *w3wp.exe*. Можно устранить эту проблему, запустив [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] под учетной записью администратора или запустив [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с консоли сервера вместо сеанса служб терминалов. 

Если ни один из этих обходных путей использовать невозможно, третий вариант — присоединение к процессу путем запуска `vsjitdebugger.exe -p <ProcessId>` из командной строки Windows. Можно определить идентификатор процесса с помощью *tlist.exe*. Для получения *tlist.exe*, скачайте и установите отладки средства для Windows, доступные в [загрузки WDK и WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_reattach"></a> Повторно подключиться к процессу

Вы можете быстро повторно подключиться к процессам, которые были ранее подключены к, выбрав **Отладка** > **повторно подключиться к процессу** (**Shift** + **Alt**+**P**). При выборе этой команды, отладчик немедленно выполняется попытка подключить к последнему процессы, к которым ранее, сначала пытаясь сопоставить идентификатор предыдущего процесса и затем, если это не удается, путем сопоставления с именем предыдущего процесса. Если соответствий не найдено, или при наличии нескольких процессов с тем же именем, **присоединение к процессу** появится диалоговое окно для выбора, чтобы правильно настроить процесс.

> [!NOTE]
> **Повторно подключиться к процессу** command появился в Visual Studio 2017.

## <a name="BKMK_Scenarios"></a> Распространенные сценарии отладки

Чтобы определить, следует ли использовать **присоединение к процессу** и какие процесс для присоединения, в следующей таблице показаны наиболее распространенные сценарии отладки, со ссылками на дополнительные инструкции, если это возможно. (Список не является исчерпывающим.) 

Для некоторых типов приложений, таких как приложения универсальных приложениях Windows (UWP), не прямое подключение к имени процесса, но использовать **отлаживать установленный пакет приложения** меню параметр в Visual Studio (см. таблицу).

Чтобы отладчик мог присоединиться к коду на языке C++, код должен предоставлять `DebuggableAttribute`. Это можно добавить в код автоматически, путем связывания с параметром [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) компоновщика.

Для отладки скриптов на стороне клиента необходимо включить отладку скриптов в браузере. Отладка клиентского сценария в Chrome, выберите **Webkit** как тип кода и в зависимости от типа приложения, может потребоваться запуск браузера в режиме отладки (тип `chrome.exe --remote-debugging-port=9222` из командной строки).

Чтобы быстро выбрать запущенный процесс для присоединения к, в Visual Studio введите **Ctrl**+**Alt**+**P**, а затем введите первую букву Имя процесса.

|Сценарий|Отладка метода|Имя процесса|Примечания и ссылки|
|-|-|-|-|
|Удаленная отладка ASP.NET 4 или 4.5 на сервере IIS|Используйте инструменты удаленной отладки и **присоединение к процессу**|*w3wp.exe*|См. в разделе [удаленная отладка ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Удаленная отладка ASP.NET Core на сервере IIS|Используйте инструменты удаленной отладки и **присоединение к процессу**|*dotnet.exe*|Для развертывания приложений, см. в разделе [публикация в IIS](https://docs.asp.net/en/latest/publishing/iis.html). Для отладки, см. в разделе [удаленной отладки ASP.NET Core на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Отладка клиентского сценария на локальном сервере IIS (только для типов поддерживаемых приложений)|Используйте **присоединение к процессу**|*Chrome.exe*, *MicrosoftEdgeCP.exe*, или *iexplore.exe*|Необходимо включить отладку скриптов. Для Chrome, необходимо также выполнить Chrome в режиме отладки и выберите **код Webkit** в **присоединить к** поля.|
|Отладка приложения C#, Visual Basic или C++ на локальном компьютере|Использовать [стандартный отладки](../debugger/getting-started-with-the-debugger.md) или **присоединение к процессу**|*\<имя_приложения > .exe*|В большинстве случаев использовать стандартный отладку и не **присоединение к процессу**.|
|Удаленная отладка классического приложения Windows|Инструменты удаленной отладки|Н/Д| См. в разделе [удаленной отладки приложения C# или Visual Basic](../debugger/remote-debugging-csharp.md) или [удаленная отладка приложения C++](../debugger/remote-debugging-cpp.md)|
|Отладка приложений ASP.NET на локальном компьютере после запуска приложения без отладчика|Используйте **присоединение к процессу**|*iiexpress.exe*|Это может быть полезно отключить учет загрузить приложения быстрее, такие как (например) при профилировании. |
|Отладка других поддерживаемых типов приложений в процессе сервера|Использовать удаленные средства (если сервер расположен удаленно) и **присоединение к процессу**|*Chrome.exe*, *iexplore.exe*, или других процессов|При необходимости используйте монитор ресурсов для определения процесса. См. в разделе [удаленной отладки](../debugger/remote-debugging.md).|
|Удаленная отладка универсальных приложениях Windows (UWP), OneCore, HoloLens и IoT приложения|Отладка установленного пакета приложения|Н/Д|См. в разделе [отладка установленного пакета приложения](debug-installed-app-package.md) вместо использования **присоединение к процессу**|
|Отладка универсальных приложениях Windows (UWP), OneCore, HoloLens и IoT приложения, вы не запускали из Visual Studio|Отладка установленного пакета приложения|Н/Д|См. в разделе [отладка установленного пакета приложения](debug-installed-app-package.md) вместо использования **присоединение к процессу**|  
  
## <a name="use-debugger-features"></a>Использование функций отладчика

Чтобы использовать все возможности отладчика Visual Studio (например, прерывания в точках останова) при присоединении к процессу, приложение должно точно соответствовать локальный источник и символы (то есть отладчик должен находиться удалось загрузить правильный [символов (.pbd) файлы](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). По умолчанию для этого отладочную сборку.

Для удаленной отладки сценариев необходимо иметь исходный код (или копию исходного кода), уже открыт в Visual Studio. Двоичные файлы скомпилированное приложение на удаленном компьютере должны поступать из одной сборки, как на локальном компьютере.

В некоторых сценариях локальной отладки отладки в Visual Studio без доступа к источнику при наличии файлов правильный символов с помощью приложения (по умолчанию для этого требуется отладочной сборки). Дополнительные сведения см. в разделе [Указание файлов символов и исходного](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> Устранение ошибок присоединения  
 При присоединении отладчика к выполняющемуся процессу этот процесс может содержать один или несколько типов кода. Типы кода, к которым может присоединиться отладчик, отображаются и выбираются в диалоговом окне **Выбор типа кода** .  
  
 Иногда отладчик может успешно присоединяться к одному типу кода, но не к другому. Такое может происходить при попытке присоединения к процессу, выполняющемуся на удаленном компьютере. На удаленном компьютере для одних типов кода могут иметься компоненты удаленной отладки, а для других — нет. Такое также может происходить при попытке присоединиться к двум или более процессам для прямой отладки базы данных. Отладка SQL поддерживает присоединение только к одному процессу.  
  
 Если отладчик может присоединиться к некоторые, но не все типы кода, вы увидите сообщение, идентифицирующее, какие типы не удалось присоединить.  
  
 Если отладчик успешно подключается хотя бы к одному типу кода, то можно приступать к отладке процесса. Но отлаживать можно будет только те типы кода, к которым удалось подсоединиться. Неподключенные код в процессе будет выполняться, но не можно установить точки останова, просматривать данные или выполнять другие операции отладки от этого кода.  
  
 Если нужны более конкретные сведения о том, почему отладчику не удалось присоединиться к некоторому типу кода, можно попытаться повторно присоединиться только к этому типу кода.  
  
 **Чтобы получить подробные сведения о причине сбоя типа кода для присоединения:**  
  
1.  Отключитесь от процесса. На **Отладка** меню, выберите **отсоединить все**.  
  
1.  Вновь подключитесь к процессу, выбрав только тип кода, который не удалось присоединить.  
  
    1.  В **присоединение к процессу** диалоговом окне выберите процесс в **доступные процессы** списка.  
  
    2.  Выберите **выберите**.  
  
    3.  В диалоговом окне **Выбор типа кода** выберите **Выполнять отладку кода следующих типов** и выберите тип кода, к которому не удалось присоединиться. Отмените выбор других типов кода.  
  
    4.  Нажмите кнопку **ОК**.  
  
    5.  В **присоединение к процессу** выберите **Attach**.  
  
    На этот раз присоединение не пройдет полностью, и будет выдано сообщение о конкретной ошибке.  
  
## <a name="see-also"></a>См. также  
 [Отладка нескольких процессов](../debugger/debug-multiple-processes.md)   
 [Отладка Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)
 