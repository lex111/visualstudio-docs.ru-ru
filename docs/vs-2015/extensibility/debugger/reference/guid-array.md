---
title: GUID_ARRAY | Документация Майкрософт
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
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4540cb45b9a80d1a0a643554b9f25c02b88570c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573035"
---
# <a name="guidarray"></a>GUID_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [GUID_ARRAY](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/guid-array).  
  
Описывает массив уникальных идентификаторов для доступных отладчиков.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagGUID_ARRAY  
{  
   DWORD dwCount;  
   GUID *Members;  
} GUID_ARRAY;  
```  
  
```csharp  
public struct GUID_ARRAY  
{  
   public uint dwCount;  
   public Guid Members;  
}  
```  
  
## <a name="terms"></a>Термины  
 dwCount  
 Число уникальных идентификаторов в массиве.  
  
 Участники  
 Массив, содержащий уникальные идентификаторы.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)

