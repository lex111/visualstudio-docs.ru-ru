---
title: IEnumDebugCustomAttributes::Next | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ff7d39bcfe255ced2f38c39cd29cd6571111978
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121083"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
Извлекает указанное число настраиваемых атрибутов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Число элементов для извлечения. Также указывает максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [out] Массив [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) объектов, которые должны заполняться в.  
  
 `pceltFetched`  
 [out] Возвращает количество элементов, фактически извлеченных в `rgelt`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше запрошенного числа элементов может быть возвращен; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)