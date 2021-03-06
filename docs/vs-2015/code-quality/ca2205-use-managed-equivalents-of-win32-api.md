---
title: 'CA2205: Используйте управляемые эквиваленты Win32 API | Документация Майкрософт'
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
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98c32eb197bb644d0e540bccea10603217342642
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591867"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: используйте управляемые эквиваленты API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2205: Используйте управляемые эквиваленты Win32 API](https://docs.microsoft.com/visualstudio/code-quality/ca2205-use-managed-equivalents-of-win32-api).

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Неуправляемого определен метод, и существует метод с эквивалентной функциональностью [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] библиотеки классов.

## <a name="rule-description"></a>Описание правила
 Неуправляемого метода используется для вызова неуправляемой функции DLL и определяется с помощью <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут, или `Declare` в Visual Basic. Это некорректно определенная платформа вызова метода может вызывать исключения среды выполнения из-за проблем, таких как неверно именованные функции, неправильное сопоставление типов данных параметров и возвращаемых значений и неверная спецификация полей, например соглашение о вызовах и символ набор. Если он доступен, обычно является более простым и надежным подвержено ошибкам, для вызова эквивалентного управляемого метода вместо определения и вызова неуправляемого метода напрямую. Вызов платформы вызов метода также может привести к дополнительным проблемам с безопасностью, которые следует учитывать.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените вызов неуправляемой функции с помощью вызова его управляемого эквивалента.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если метод в качестве замены не предоставляет необходимую функциональность.

## <a name="example"></a>Пример
 В следующем примере показан платформы вызвать определение метода, который нарушает правило. Кроме того вызовы платформы вызова метода и показаны эквивалентные управляемый метод.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1404: вызывайте GetLastError сразу после P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: переместите P/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: необходимо наличие точек входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



