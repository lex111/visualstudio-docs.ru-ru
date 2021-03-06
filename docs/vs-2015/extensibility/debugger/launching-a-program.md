---
title: Запуск программы | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af5987f793e6f0164654f280f8417494066e3e5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568768"
---
# <a name="launching-a-program"></a>Запуск программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [запуск программы](https://docs.microsoft.com/visualstudio/extensibility/debugger/launching-a-program).  
  
Пользователи, желающие отладки программы, можно нажать клавишу F5, чтобы запустить отладчик в интегрированной среде разработки. Таким образом вы сможете ряд событий, которые в конечном счете приводят к интегрированной среде разработки, подключение к модуля отладки (DE), то есть в свою очередь подключены или присоединения к программе следующим образом:  
  
1.  IDE сначала вызывает пакет проекта для получения параметры отладки для активного проекта решения. Параметры включают начальный каталог, переменные среды, порт, в котором будет выполняться программа и DE для использования для создания программы, если указана. Эти параметры передаются в пакет отладки.  
  
2.  Если указан DE, DE вызывает операционной системы, чтобы запустить программу. В результате запуска программы, загружается среды времени выполнения программы. Например если программа создается на языке MSIL, среда CLR будет вызываться для запуска программы.  
  
     - или -  
  
     Если DE не указан, порт вызывает операционной системы, чтобы запустить программу, что приводит к среде выполнения программы для загрузки.  
  
    > [!NOTE]
    >  Если DE используется для запуска программы, вполне вероятно, что же DE будут присоединены к программе.  
  
3.  В зависимости от того DE или порт запустила программу DE или среды выполнения создает описание программы, или узел затем уведомляет порт, на котором выполняется программа.  
  
    > [!NOTE]
    >  Рекомендуется, среде выполнения создать узел программы, так как узел программа представляет собой упрощенный программы, которые можно отлаживать. Нет необходимости загрузки всей DE, чтобы создать и зарегистрировать узел программы. Если DE предназначен для запуска в процессе интегрированной среды разработки, но не IDE действительно работает, должен быть компонентом, который можно добавить узел программы к порту.  
  
 Только что созданный программы, а также все другие программы, связанные с несвязанных, запустить или подключенные к одной интегрированной среде разработки, создания сеанса отладки.  
  
 Программным образом, при первом нажатии **F5**, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]в отладочный пакет вызывает пакет проекта (она связана с типом запуска программы) через <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> метод, который в свою очередь заполняет <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> структуру с параметры отладки для активного проекта решения. Эта структура передается обратно отладки пакета путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> метод. Размер пакета отладки создает экземпляр диспетчер отладки сеансов (SDM), которая запускает программу, отладки и все связанные с ней отладчиков.  
  
 Одним из аргументов, переданных SDM является идентификатор GUID для DE, который будет использоваться для запуска программы.  
  
 Если идентификатор GUID DE не `GUID_NULL`, SDM совместно создает DE, а затем вызывает его [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) метод, чтобы запустить программу. Например, если программа записывается в машинном коде, затем `IDebugEngineLaunch2::LaunchSuspended` , скорее всего, вызовет `CreateProcess` и `ResumeThread` (функции Win32), чтобы запустить программу.  
  
 В результате запуска программы, загружается среды времени выполнения программы. DE или среды выполнения создает [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейса для описания программы и передает этот интерфейс для [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) для уведомления порт, который программа запущена.  
  
 Если `GUID_NULL` передается, то порт запускает программу по. После запуска программы, среда выполнения создает `IDebugProgramNode2` интерфейса для описания программы и передает его `IDebugPortNotify2::AddProgramNode`. Получает уведомление и порт, на котором выполняется программа. Затем SDM Присоединяет отладчик к выполняющейся программе.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Уведомление порта](../../extensibility/debugger/notifying-the-port.md)  
 Объясняет, что происходит после запуска программы и порта уведомляется.  
  
 [Присоединение после запуска](../../extensibility/debugger/attaching-after-a-launch.md)  
 Документы, когда сеанс отладки будет готов для присоединения к программе DE.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.

