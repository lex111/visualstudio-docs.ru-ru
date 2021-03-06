---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9d80a7257a19fb9bb9a638c73002f73e7899d48
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561043"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaAddressMap::put_relativeVirtualAddressEnabled](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled).  
  
Позволяет клиенту включить или отключить вычисление и использование относительные виртуальные адреса (RVA).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 NewVal  
 [in] Значение `TRUE` для включения, или `FALSE` для отключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Адреса для отладки объектов, описанные по интерфейсов доступа к интерфейсу отладки, а также относительно исполняемого файла изображения базовый, могут быть получены как относительные виртуальные адреса.  
  
 Использование RVA включена в том случае, если сегменты изначально загружаются из PDB-файл. Чтобы получить текущее состояние использования RVA, вызовите [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) метод.  
  
 `put_relativeVirtualAddress` Метод должен вызываться для включения RVA после успешного вызова [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) метод устанавливает новый образ заголовки.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)



