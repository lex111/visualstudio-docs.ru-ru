---
title: 'CA2102: Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков | Документация Майкрософт'
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
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1e798f7c8377d0bde569c9c0e1c10cc299b28af6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592345"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков](https://docs.microsoft.com/visualstudio/code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers).

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член в сборке, которая не помечен атрибутом <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> или помечен `RuntimeCompatibility(WrapNonExceptionThrows = false)` содержит блок catch, обрабатывающий <xref:System.Exception?displayProperty=fullName> и не содержит сразу после общий блок catch. Это правило не учитывает [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] сборок.

## <a name="rule-description"></a>Описание правила
 Блок catch, обрабатывающий <xref:System.Exception> перехватывает все исключения с общеязыковой спецификацией (CLS). Тем не менее она не перехватывает несовместимые с CLS исключения. Несовместимое с CLS исключения могут создаваться из машинного кода или из управляемого кода, который был создан корпорацией Майкрософт промежуточного языка MSIL Assembler. Обратите внимание, что C# и [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] компиляторов не разрешает несовместимые с CLS исключения исключение и [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] не перехватывает несовместимые с CLS исключения. Если предполагается блока catch обрабатывать все исключения, используйте следующий синтаксис блока общего перехвата.

-   В C#: `catch {}`

-   C++: `catch(...) {}` или `catch(Object^) {}`

 Необработанное несовместимые с CLS исключения, несовместимые с проблемой безопасности при удалении ранее предоставленные разрешения в блоке catch. Так как несовместимые с CLS исключения не перехватываются, с повышенным уровнем разрешений может запустить вредоносный метод, который создает несовместимые с CLS исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, когда цель состоит в том, чтобы перехватывать все исключения, заменить или добавить общий блок catch или пометить сборку `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Если в блоке catch удаляются разрешения, повторяющиеся функциональные возможности в целом блок catch. Если это не должны обрабатывать все исключения, замените блок catch, который обрабатывает <xref:System.Exception> с блоки catch, которые обрабатывают исключения определенных типов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если в блок try не содержит операторов, которые могут создавать несовместимые с CLS исключение. Так как любой машинный или управляемый код может вызвать несовместимые с CLS исключение, это требует знания весь код, который может выполняться во всех путях кода внутри блока try. Обратите внимание, что несовместимые с CLS исключения не вызываются средой CLR.

## <a name="example"></a>Пример
 Следующий пример показывает класс MSIL, который создает исключение совместимые с CLS.

```
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example"></a>Пример
 Пример метода, содержащего общий блок catch, соответствующий правилу.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Скомпилируйте предыдущих примерах следующим образом.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Связанные правила
 [CA1031: не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>См. также
 [Исключения и обработка исключений](http://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (ассемблер IL)](http://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [переопределения проверок безопасности](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [независимость от языка и независимые от языка компоненты](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



