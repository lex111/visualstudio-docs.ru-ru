---
title: MODULE_FLAGS | Документация Майкрософт
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
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 224a6db4b6c4860a2bf9a0b326319a3be1efc6a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559569"
---
# <a name="moduleflags"></a>MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [MODULE_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/module-flags).  
  
Используется для описания модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Участники  
 MODULE_FLAG_NONE  
 Указывает модуль не.  
  
 MODULE_FLAG_SYSTEM  
 Указывает системном модуле.  
  
 MODULE_FLAG_SYMBOLS  
 Задает модуль записи символов.  
  
 MODULE_FLAG_64BIT  
 Задает 64-разрядного модуля.  
  
 MODULE_FLAG_OPTIMIZED  
 Указывает, что модуль был оптимизирован. Это состояние отражается в **модули** окна.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Указывает, что модуль не был оптимизирован. Это состояние отражается в **модули** окна. Это состояние по умолчанию.  
  
## <a name="remarks"></a>Примечания  
 Используется для `m_dwModuleFlags` членом [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры.  
  
 Эти флаги могут быть объединены с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)

