---
title: IDebugDocumentPositionOffset2 | Документация Майкрософт
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
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10c71340b6ad6c7e76753b40c3bef55d8e7e606
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562210"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugDocumentPositionOffset2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentpositionoffset2).  
  
Представляет позицию в файле исходного кода как смещение в буфере символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуется интегрированной среды разработки и потребляемых отладчиков.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Извлекает диапазон для текущей позиции документа.|  
  
## <a name="remarks"></a>Примечания  
 Возвращает те же сведения, что [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) в `char` смещений от начала документа. Это представляет документ, как он будет существовать на диске, то есть в одномерный массив символов, а не сведения строки и столбца, который обычно возвращается.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

