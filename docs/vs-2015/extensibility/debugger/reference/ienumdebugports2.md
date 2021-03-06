---
title: IEnumDebugPorts2 | Документация Майкрософт
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
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ff7eac1da5cba43bf93a352e571c7a1f912932b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571078"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEnumDebugPorts2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugports2).  
  
Этот интерфейс перечисляет порты машинного или порта поставщика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщика пользовательского порта реализует этот интерфейс для представления список портов, созданные поставщиком. Visual Studio реализует этот интерфейс для поддержки свой собственный поставщик порта.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) для получения этого интерфейса, представляющий список портов, созданные поставщика порта. Вызовите [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) для получения этого интерфейса, представляющий список портов, которые были сохранены на диск.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPorts2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Извлекает указанное число портов в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Пропускает заданное число портов в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Получает количество портов в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует этот интерфейс, помогающий заполнить Мой список портов, используемых для присоединения к процессам.  
  
 Обычно модуль отладки не использует этот интерфейс.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

