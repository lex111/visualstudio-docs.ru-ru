---
title: ': Ca2242 NaN правильно | Документация Майкрософт'
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
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcbfd5e5bd52be2919835cbe5bdfb06119f2a688
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591666"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: правильно выполняйте проверку NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2242: правильно выполняйте проверку NaN](https://docs.microsoft.com/visualstudio/code-quality/ca2242-test-for-nan-correctly).

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выражение проверяет значение на <xref:System.Single.NaN?displayProperty=fullName> или <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Double.NaN?displayProperty=fullName>, который представляет не является числовым, результаты при арифметической операции не определено. Любое выражение, которое проверяет равенство между значениями и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает `false`. Любое выражение, которое проверяет неравенство значение и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила и точно определить, представляет ли значение <xref:System.Double.NaN?displayProperty=fullName>, использовать <xref:System.Single.IsNaN%2A?displayProperty=fullName> или <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два выражения, которые неправильно проверяют значение с <xref:System.Double.NaN?displayProperty=fullName> и выражение, которое правильно использует <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]



