---
title: 'CA1034: Вложенные типы не должны быть видимыми | Документация Майкрософт'
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
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5edfdca7fe3834160a7120528b56a2770924bf83
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591687"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: вложенные типы не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1034: вложенные типы не должны быть видимыми](https://docs.microsoft.com/visualstudio/code-quality/ca1034-nested-types-should-not-be-visible).

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне тип содержит объявление видимый извне тип. Вложенных перечислений и защищенные типы будут исключены из этого правила.

## <a name="rule-description"></a>Описание правила
 Вложенный тип — это тип, объявленный внутри области другого типа. Вложенные типы полезны для инкапсуляции закрытых сведений о реализациях содержащего типа. В силу этого вложенные типы не должны быть видимыми для внешнего кода.

 Не используйте вложенные типы, видимые извне, для логической группировки или во избежание конфликтов имен. Вместо этого используйте пространства имен.

 Вложенные типы включают понятие доступности членов некоторые программисты не всегда очевидно.

 Защищенные типы могут использоваться в подклассы и вложенные типы в сценариях расширенной настройки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если не предполагается вложенный тип, видимый извне, измените доступность типов. В противном случае удалите вложенного типа из его родительского элемента. Если вложение предназначена для категоризации вложенного типа, следует используйте пространство имен для создания иерархии.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]



