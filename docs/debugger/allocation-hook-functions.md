---
title: Функции-ловушки выделения | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c8a051641811da3658ffe556982c67649704069
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433360"
---
# <a name="allocation-hook-functions"></a>Функции-ловушки выделения
Функции-ловушки выделения, установленные с помощью [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), вызываются всякий раз при выделении, перераспределить или освобождении памяти. Можно использовать этот тип ловушек для различных целей. Использовать для тестирования, как приложение обрабатывает ситуации недостатка памяти, например, для оценки шаблонов выделения, или регистрации данных о выделении для дальнейшего анализа.  
  
> [!NOTE]
>  Имейте в виду ограничения об использовании функций библиотеки времени выполнения C в функции-ловушки выделения, описанных в [ловушки выделения и выделения памяти времени выполнения C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Функция-ловушка выделения должна иметь прототип как в следующем примере:  
  
```cpp
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Указатель, передаваемый [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) имеет тип **_CRT_ALLOC_HOOK**, как определено в CRTDBG. H:  
  
```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Когда библиотека CRT вызывает ловушку, *nAllocType* аргумент указывает, какие выделения операции будет осуществляться (**_HOOK_ALLOC**, **_HOOK_REALLOC**, или **_HOOK_FREE**). В бесплатной или перераспределения `pvData` содержит указатель на статье пользователя освобождаемого блока. Тем не менее для выделения памяти этот указатель имеет значение null, так как не произошла операция выделения. Остальные аргументы содержат размер запрашиваемого выделения, его тип блока, номер последующего запроса связанный с ней указатель на имя файла. Если он доступен, аргументы также включать номер строки, в которой было сделано выделение. После того как функция-ловушка выполнит анализ и другие запрограммированные автором, она должна вернуть или **TRUE**, означает, что операция выделения может продолжаться, или **FALSE**, указывая, что Операция должна завершиться ошибкой. Простая ловушка этого типа может проверить количество выделенной до настоящего момента памяти и вернуть **FALSE** случае превышения лимита. В таком случае в приложении могут возникать ошибки выделения памяти, которые обычно возникают только при большой нехватке доступной памяти. Более сложные ловушки могут отслеживать структуру выделения, анализировать использование памяти или сообщать о возникновении какой-либо определенной ситуации.  
  
## <a name="see-also"></a>См. также  
 [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
