---
title: IDebugCoreServer3::EnableAutoAttach | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf32eb5d8771f95ec155a93d1fe1e770e0cc2d52
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108499"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Включает автоматическое присоединение для указанного отладчики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rgguidSpecificEngines`  
 [in] Массив идентификаторов GUID для каждого ядра отладки для пометки как автоматическое присоединение.  
  
 `celtSpecificEngines`  
 [in] Количество обработчиков, указанный в `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] Начальный URL-адрес для использования при присоединении автоматически.  
  
 `pbstrSessionID`  
 [out] Идентификатор сеанса, который был подключен автоматически.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Один код ошибки- `E_AUTO_ATTACH_NOT_REGISTERED`, указывающая, что фабрика класса auto-attach не был зарегистрирован.  
  
## <a name="remarks"></a>Примечания  
 При запуске программы, связанные с указанным URL-адрес, указанный отладчики автоматически запущен и присоединенного.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)