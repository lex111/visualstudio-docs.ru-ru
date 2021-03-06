---
title: 'CA1010: коллекции должны реализовывать универсальный интерфейс'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f79a0e4fcb9cf4f82b85e9d62ffa51ef969293c7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551003"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: коллекции должны реализовывать универсальный интерфейс
|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Видимый извне тип реализует <xref:System.Collections.IEnumerable?displayProperty=fullName> интерфейса, но не реализует <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> интерфейс и включенная сборка предназначена [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Это правило не учитывает типы, реализующие <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Чтобы расширить возможности использования коллекции, реализуйте один из универсальных интерфейсов коллекции. Вы можете использовать коллекцию для заполнения типы универсальных коллекций, таких как следующие:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте один из следующих универсальных интерфейсов:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила; Тем не менее коллекция будет иметь более ограниченное использование.

## <a name="example-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В примере показан класс (ссылочный тип), является производным от неуниверсального `CollectionBase` класс, который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

### <a name="comments"></a>Комментарии
 Чтобы устранить нарушение этого нарушения, должны реализовывать универсальные интерфейсы или измените базовый класс для типа, который уже реализует обеих универсальных и неуниверсальных интерфейсов, таких как `Collection<T>` класса.

## <a name="fix-by-base-class-change"></a>Исправить путем замены базового класса

### <a name="description"></a>Описание
 В следующем примере нарушение устраняется путем изменения базового класса коллекции с неуниверсального `CollectionBase` класса к общим `Collection<T>` (`Collection(Of T)` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) класса.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

### <a name="comments"></a>Комментарии
 Изменение базового класса уже выпущенного класса считается критическим изменением для существующих потребителей.

## <a name="fix-by-interface-implementation"></a>Исправление посредством реализации интерфейсов

### <a name="description"></a>Описание
 В следующем примере устраняется нарушение путем реализации этих универсальных интерфейсов: `IEnumerable<T>`, `ICollection<T>`, и `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, и `IList(Of T)` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)