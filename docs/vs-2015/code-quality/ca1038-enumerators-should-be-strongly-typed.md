---
title: 'CA1038: Перечислители должны быть строго типизированы | Документация Майкрософт'
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
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d0bc23e78580329443c06cd419febd50e3d3db27
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591309"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: перечислители должны быть строго типизированы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1038: перечислители должны быть строго типизированы](https://docs.microsoft.com/visualstudio/code-quality/ca1038-enumerators-should-be-strongly-typed).

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.Collections.IEnumerator?displayProperty=fullName> , но не предоставляет строго типизированную версию <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> свойство. Типы, которые являются производными от следующих типов будут исключены из этого правила:

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 Это правило требует <xref:System.Collections.IEnumerator> реализации предоставляли строго типизированную версию <xref:System.Collections.IEnumerator.Current%2A> свойство, чтобы пользователям не придется приводить возвращаемое значение к строгому типу, при использовании функциональных возможностей интерфейса. В этом правиле предполагается, что тип, реализующий <xref:System.Collections.IEnumerator> содержит коллекцию экземпляров типа, которое строже, чем <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализовать свойство интерфейса явным образом (он объявляется как `IEnumerator.Current`). Добавьте открытый строго типизированную версию свойства, объявленные как `Current`, который будет возвращать строго типизированный объект.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, при реализации перечислитель объектно ориентированного для использования с коллекцией на базе объектов, например двоичного дерева. Типы, расширяющие новая коллекция будет определять строго типизированный перечислитель и предоставлять строго типизированные свойства.

## <a name="example"></a>Пример
 В следующем примере показано правильный способ реализации строго типизированный <xref:System.Collections.IEnumerator> типа.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1035: в составе реализаций ICollection есть строго типизированные элементы](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>См. также
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>



