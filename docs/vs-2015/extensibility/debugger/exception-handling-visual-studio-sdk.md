---
title: Исключение, обработка (пакет SDK для Visual Studio) | Документация Майкрософт
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
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e42e4dbe18b0d2fe6da522d24d493270518e884e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572966"
---
# <a name="exception-handling-visual-studio-sdk"></a>Обработка исключений (пакет SDK для Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [обработка исключений (Visual Studio SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/exception-handling-visual-studio-sdk).  
  
Ниже описывается процесс, происходящее при возникновении исключения.  
  
## <a name="exception-handling-process"></a>Процесс обработки исключений  
  
1.  Когда исключение, но прежде чем он обрабатывается обработчиком исключений в отлаживаемой программы, модуль отладки (DE) отправляет [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) в диспетчер отладки сеансов (SDM) как событие остановки. `IDebugExceptionEvent2` Отправляется, если только параметры для исключения (указано в диалоговом окне "исключения" в пакете отладки) укажите, что пользователь хочет остановить при возникновении уведомления о первом этапе обработки исключений.  
  
2.  Вызовы SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) для получения свойства исключения.  
  
3.  Вызовы отладки пакета [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) для определения, какие параметры пользователя.  
  
4.  Размер пакета отладки запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно исключения первого шанса.  
  
5.  Если пользователь выбрал в том продолжить, SDM вызывает [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Если метод возвращает значение S_OK, вызывает [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         - или -  
  
         Если метод возвращает значение S_FALSE, программа отлаживаемой дается второй шанс для обработки исключения.  
  
6.  Если отлаживаемой программы не имеет обработчика для второй возможности захвата исключения, DE отправляет `IDebugExceptionEvent2` для SDM как **EVENT_SYNC_STOP**.  
  
7.  Размер пакета отладки запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно исключения первого шанса.  
  
8.  Вызовы отладки пакета [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) для определения, какие параметры пользователя.  
  
9. Размер пакета отладки запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно второй возможности захвата исключений.  
  
10. Если метод возвращает значение S_OK, вызывает `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)

