---
title: 'CA2202: не удаляйте объекты несколько раз'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e805cb76ebe4c216b456f65ea3264f8f25561cc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548612"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: не удаляйте объекты несколько раз

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Реализация метода содержит пути кода, которые могут стать причиной многократного вызова <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> или эквивалентного метода Dispose, например, метода Close() для некоторых типов, на тот же объект.

## <a name="rule-description"></a>Описание правила

Объект правильно реализована <xref:System.IDisposable.Dispose%2A> метод может вызываться несколько раз без вызова исключения. Тем не менее, это не гарантируется и для предотвращения создания <xref:System.ObjectDisposedException?displayProperty=fullName> не следует вызывать <xref:System.IDisposable.Dispose%2A> более чем один раз для объекта.

## <a name="related-rules"></a>Связанные правила

- [CA2000: удалите объекты до того, как будет потеряна область действия](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените реализацию таким образом, независимо от того, путь кода, <xref:System.IDisposable.Dispose%2A> вызывается только один раз для объекта.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Даже если <xref:System.IDisposable.Dispose%2A> для объекта известно, можно безопасно вызывать несколько раз, его реализация может измениться в будущем.

## <a name="example"></a>Пример

Вложенные `using` инструкций (`Using` в Visual Basic) может вызвать нарушения CA2202 предупреждения. Если ресурс IDisposable вложенного внутреннего `using` инструкция содержит ресурс внешнего `using` инструкции `Dispose` метод вложенного ресурса освобождает содержимом ресурсе. При возникновении такой ситуации, `Dispose` метод, внешнего `using` оператор пытается ликвидировать свой ресурс еще раз.

В следующем примере <xref:System.IO.Stream> объект, создаваемый во внешнем инструкцией освобождается в конце внутреннего использования оператора в методе Dispose <xref:System.IO.StreamWriter> , содержащий `stream` объекта. В конце внешний `using` инструкции `stream` объект освобождается во второй раз. Второй выпуск является нарушением CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Пример

Чтобы устранить эту проблему, используйте `try` / `finally` блока вместо внешнего `using` инструкции. В `finally` block, убедитесь, что `stream` ресурс не имеет значение null.

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>См. также

- <xref:System.IDisposable?displayProperty=fullName>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)