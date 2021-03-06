---
title: 'CA1023: Индексы не должны быть многомерными | Документация Майкрософт'
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
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e1b1022484db26e6ff8fbc0046333f187753bb53
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591111"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: индексы не должны быть многомерными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1023: индексы не должны быть многомерными](https://docs.microsoft.com/visualstudio/code-quality/ca1023-indexers-should-not-be-multidimensional).

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный индексатор, использующий более одного индекса.

## <a name="rule-description"></a>Описание правила
 Индексаторы, то есть индексированные свойства, должны использовать один индекс. Многомерные индексаторы могут существенно снизить удобство использования библиотеки. Если в программе требуется несколько индексов, пересмотрите ли тип логическое хранилище данных. В противном случае используется метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, изменить структуру использовать единственный целочисленный или строковый индекс или использовать метод вместо индексатора.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только после тщательной проверки необходимости использовать нестандартный индексатор.

## <a name="example"></a>Пример
 В следующем примере показано типом, `DayOfWeek03`, с помощью многомерных индексатора, которое нарушает правило. Индексатор можно рассматривать как тип преобразования и поэтому более качественной представляется как метод. Изменен механизм функционирования тип в `RedesignedDayOfWeek03` в соответствии с правилом.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1043: используйте целый или строковый аргумент для индексаторов](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)



