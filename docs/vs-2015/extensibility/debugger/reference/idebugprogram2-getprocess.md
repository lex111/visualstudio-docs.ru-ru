---
title: IDebugProgram2::GetProcess | Документация Майкрософт
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
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5e40776af6011d612d4af79eca70928b6c39edb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570840"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgram2::GetProcess](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getprocess).  
  
Получение, на котором выполняется эта программа, в процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppProcess`  
 [out] Возвращает [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, представляющий процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если отладчик (DE) реализует [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) интерфейс, DE реализация этого метода всегда должны возвращать `E_NOTIMPL` поскольку DE не может определить, какой процесс, он выполняется в и, следовательно, не может удовлетворять реализация этого метода.  
  
 Реализация `IDebugEngineLaunch2` интерфейс означает, что DE необходимо знать, как создать процесс; таким образом, DE реализация [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) могут узнать, какой процесс выполняется в интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

