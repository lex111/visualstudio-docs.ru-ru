---
title: 'CA1505: Избегайте кода, неудобного для поддержки | Документация Майкрософт'
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
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee836af1ee0030c3eea56e12ea5fe767c4b7255b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591684"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505. Избегайте кода, неудобного для поддержки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1505: Избегайте кода, неудобного для поддержки](https://docs.microsoft.com/visualstudio/code-quality/ca1505-avoid-unmaintainable-code).

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип или метод имеет низкий индекс обслуживаемости.

## <a name="rule-description"></a>Описание правила
 Индекс удобства поддержки вычисляется с помощью следующих метрик: строки кода, объем программы и сложность организации циклов. Программа тома — это мера трудности понимания типа или метода, основанный на количестве операторов и операндов в коде. Сложность организации циклов — это мера сложности структурного типа или метода. Дополнительные сведения о метриках кода в [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Низкий индекс обслуживаемости указывает, что тип или метод, вероятно, трудно поддерживать и будет хорошим кандидатом для переработки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, измените тип или метод и попробуйте разделить ее на сокращенный и более точный типы или методы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Исключите это предупреждение, когда тип или метод по-прежнему считается простым в обслуживании, несмотря на своего большого размера или типа или метода нельзя разделить.

## <a name="see-also"></a>См. также
 [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md) [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



