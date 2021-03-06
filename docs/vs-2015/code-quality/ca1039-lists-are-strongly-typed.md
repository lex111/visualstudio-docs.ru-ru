---
title: 'CA1039: Списки обладают строгой типизацией | Документация Майкрософт'
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
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e20be039d2b743fecf15d855bc5f32fd65a75ce9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592348"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: списки обладают строгой типизацией
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1039: списки обладают строгой типизацией](https://docs.microsoft.com/visualstudio/code-quality/ca1039-lists-are-strongly-typed).

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.Collections.IList?displayProperty=fullName> , но не предоставляет строго типизированный метод для одного или нескольких из следующих:

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>Описание правила
 Это правило требует <xref:System.Collections.IList> реализации предоставляли строго типизированные элементы, чтобы пользователям не придется приводить аргументы к <xref:System.Object?displayProperty=fullName> введите при использовании функциональных возможностей интерфейса. <xref:System.Collections.IList> Интерфейс реализуется классом коллекции объектов, доступных по индексу. В этом правиле предполагается, что тип, реализующий <xref:System.Collections.IList> делает это для управления коллекцией экземпляров типа, которое строже, чем <xref:System.Object>.

 <xref:System.Collections.IList> реализует <xref:System.Collections.ICollection?displayProperty=fullName> и <xref:System.Collections.IEnumerable?displayProperty=fullName> интерфейсов. Если вы реализуете <xref:System.Collections.IList>, необходимо предоставить обязательные строго типизированные члены для <xref:System.Collections.ICollection>. Если расширение объектов в коллекции <xref:System.ValueType?displayProperty=fullName>, необходимо предоставить строго типизированный элемент для <xref:System.Collections.IEnumerable.GetEnumerator%2A> во избежание снижение производительности, вызванные упаковки-преобразования; это не является обязательным, если объекты коллекции имеют ссылочный тип.

 Чтобы обеспечить соответствие с этим правилом, реализовать члены интерфейса явно с помощью имен в форме InterfaceName.InterfaceMemberName, такие как <xref:System.Collections.IList.Add%2A>. К явным членам интерфейса используйте типы данных, которые объявлены в интерфейсе. Реализовать строго типизированные элементы, используя имена членов интерфейса, такие как `Add`. Объявите строго типизированные члены как открытые и объявления параметров и возвращаемых значений строгого типа, который управляется в коллекции. Строгие типы замените слабый типы, такие как <xref:System.Object> и <xref:System.Array> , объявленные в интерфейсе.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явно реализовать <xref:System.Collections.IList> членов и предоставить строго типизированные альтернативные варианты для членов, которые упоминались ранее. Для кода, который правильно реализует <xref:System.Collections.IList> интерфейс, а также предоставляет требуемый строго типизированные элементы, см. ниже.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 При реализации новой коллекции на базе объектов, например связанный список, где типы, расширяющие новую коллекцию, определяют строгий тип, отключайте предупреждение из этого правила. Эти типы должны соответствуют данному правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
 В следующем примере тип `YourType` расширяет <xref:System.Collections.CollectionBase?displayProperty=fullName>, так же как и все строго типизированных коллекций. Обратите внимание, что <xref:System.Collections.CollectionBase> предоставляет явную реализацию метода <xref:System.Collections.IList> интерфейс для вас. Таким образом, необходимо указать только строго типизированные члены для <xref:System.Collections.IList> и <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1035: в составе реализаций ICollection есть строго типизированные элементы](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: перечислители должны быть строго типизированы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>См. также
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>



