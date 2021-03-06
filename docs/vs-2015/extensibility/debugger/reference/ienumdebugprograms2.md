---
title: IEnumDebugPrograms2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2871a64ce618d03a96900d916a56fb0c598e47e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564195"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEnumDebugPrograms2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugprograms2).  
  
Этот интерфейс перечисляет программ, работающих в текущем сеансе отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список отлаживаемых по DE программ.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Visual Studio вызывает [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) для получения этого интерфейса. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не используется средой Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPrograms2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Извлекает указанное число программ в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропускает заданное число программ в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Получает количество программ в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует этот интерфейс, чтобы:  
  
-   Заполнение **модули** окна (путем вызова [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) и последующего вызова [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) на каждую программу).  
  
-   Заполнение **присоединение к процессу** список (путем вызова `IDebugProcess2::EnumPrograms` и последующего вызова [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на каждом [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для получения [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) интерфейс).  
  
-   Создать список DEs, способное отлаживать каждой программы в процессе (с помощью [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Применение обновлений, изменить и продолжить "(ENC) для каждой программы (путем вызова IDebugProcess2::EnumPrograms и последующего вызова [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

