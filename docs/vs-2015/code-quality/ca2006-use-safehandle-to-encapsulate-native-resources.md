---
title: 'CA2006: Используйте SafeHandle для инкапсуляции машинных ресурсов | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 08eed3577a8c225a69c5a3a8a9b4a1348656bd3f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591675"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: используйте SafeHandle для инкапсуляции машинных ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2006: используйте SafeHandle для инкапсуляции машинных ресурсов](https://docs.microsoft.com/visualstudio/code-quality/ca2006-use-safehandle-to-encapsulate-native-resources).

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Категория|Microsoft.Reliability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Управляемый код использует <xref:System.IntPtr> обратиться к собственным ресурсам.

## <a name="rule-description"></a>Описание правила
 Использование `IntPtr` в управляемом коде может свидетельствовать о потенциальных проблемах безопасности и надежности. Все случаи использования `IntPtr` необходимо изучить, чтобы определить ли использование <xref:System.Runtime.InteropServices.SafeHandle> , или аналогичную технологию, на его месте. Проблемы возникают в том случае, если `IntPtr` представляет некоторые машинный ресурс, например память, дескриптор файла или сокета, что управляемый код считается владельцем. Если управляемый код, которому принадлежит ресурс, он должен также освободить машинные ресурсы, связанные с ним, так как Невыполнение этого требования приведет утечки ресурсов.

 В таких случаях проблемы безопасности или надежности также будет существовать, если многопоточный доступ может быть `IntPtr` и способ освобождения ресурса, представленного `IntPtr` предоставляется. Эти проблемы связаны перезапуск с `IntPtr` значение освобождения ресурса во время одновременного использования ресурса выполняется в другом потоке. Это может привести к конкуренции, где один поток можно считывать или записывать данные, связанные с неправильный ресурс. Например, если дескриптор операционной системы, как хранение в типе `IntPtr` и позволяет пользователям следует вызвать оба **закрыть** и любой другой метод, использующий этот дескриптор одновременно и без какого-либо рода синхронизации, код содержит вторичное использование дескриптора проблема.

 Это проблема повторного использования дескриптора может привести к повреждению данных, а иногда и уязвимость системы безопасности. `SafeHandle` и его одноуровневый класс <xref:System.Runtime.InteropServices.CriticalHandle> предоставляют механизм для инкапсуляции собственный дескриптор для ресурса, так что можно избежать такой проблемы с потоками. Кроме того, можно использовать `SafeHandle` и того же уровня класса `CriticalHandle` для других проблем многопоточности, например, тщательно управление временем существования управляемых объектов, которые содержат копию собственный дескриптор через вызовы собственных методов. В этом случае его можно удалить вызовы `GC.KeepAlive`. Затратам на тайском языке производительности взимается при использовании `SafeHandle` и в меньшей степени `CriticalHandle`, часто можно сократить до тщательного проектирования.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Преобразовать `IntPtr` использования `SafeHandle` для безопасного управления неуправляемыми ресурсами. См. в разделе <xref:System.Runtime.InteropServices.SafeHandle> справочном разделе примеры.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует подавлять это предупреждение.

## <a name="see-also"></a>См. также
 <xref:System.IDisposable>



