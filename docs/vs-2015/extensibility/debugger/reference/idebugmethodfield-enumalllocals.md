---
title: IDebugMethodField::EnumAllLocals | Документация Майкрософт
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
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce7db92adfed5558eaaa86e2e84af51da9059020
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557920"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugMethodField::EnumAllLocals](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmethodfield-enumalllocals).  
  
Создает перечислитель для всех локальных переменных метода, в том числе создаются внутри организации, с помощью компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объект, представляющий адрес отладки в методе, указывающая на определенной области или контекста.  
  
 `ppLocals`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список всех локальных переменных в указанной области; в противном случае возвращает значение null, указывающее, без локальных элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, или возвращает значение S_FALSE, если нет локальных переменных. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Перечисляются только те переменные, определенные внутри блока, который содержит адрес заданной отладочной. Этот метод включает в себя все локальные переменные, создаваемые компилятором. Если все, которые требуется явно определенные в источнике, вызов "Локальные" [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) метод.  
  
 Метод может содержать несколько контекстов или блоки области.  
  
## <a name="see-also"></a>См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)

