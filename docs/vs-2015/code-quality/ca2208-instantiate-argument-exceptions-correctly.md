---
title: 'CA2208: Правильно создавайте экземпляры исключений аргументов | Документация Майкрософт'
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
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba99cddfe42e1b6699dba4fa665302581aa68cdc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591937"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: правильно создавайте экземпляры аргументов исключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2208: правильно создавайте экземпляры исключений аргументов](https://docs.microsoft.com/visualstudio/code-quality/ca2208-instantiate-argument-exceptions-correctly).

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Возможны следующие причины следующих ситуациях.

-   Выполняется вызов конструктора по умолчанию (без параметров) типа исключения, которое является или является производным от [System.ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

-   Неправильный аргумент строки передается параметризованному конструктору типа исключения, которое является или является производным от [System.ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Описание правила
 Вместо вызова конструктора по умолчанию, вызовите одну из перегрузок конструктора, что позволяет более понятное сообщение об исключении, должны быть предоставлены. Сообщение об исключении должно предназначаться разработчикам и понятно объяснить условие ошибки и как исправить или избежать исключения.

 Сигнатуры двух и строка конструкторы <xref:System.ArgumentException> и его производные типы не соответствуют по отношению к `message` и `paramName` параметров. Убедитесь, что эти конструкторы вызываются с правильными аргументами. Сигнатуры выглядят следующим образом:

 <xref:System.ArgumentException>(строка `message`)

 <xref:System.ArgumentException>(строка `message`, строка `paramName`)

 <xref:System.ArgumentNullException>(строка `paramName`)

 <xref:System.ArgumentNullException>(строка `paramName`, строка `message`)

 <xref:System.ArgumentOutOfRangeException>(строка `paramName`)

 <xref:System.ArgumentOutOfRangeException>(строка `paramName`, строка `message`)

 <xref:System.DuplicateWaitObjectException>(строка `parameterName`)

 <xref:System.DuplicateWaitObjectException>(строка `parameterName`, строка `message`)

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите конструктор, который принимает сообщение и имя параметра и убедитесь, что аргументы имеют правильный тип <xref:System.ArgumentException> вызова.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, только в том случае, если параметризованный конструктор вызывается с правильными аргументами.

## <a name="example"></a>Пример
 В следующем примере конструктор, который неправильно создает экземпляр типа ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Пример
 В следующем примере устраняется нарушение путем переключения аргументы конструктора.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]



