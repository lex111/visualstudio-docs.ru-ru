---
title: 'CA1401: P / Invokes не должны быть видимыми | Документация Майкрософт'
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
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c376c2ae8a1d09ff040d9929617c75037ac5d28
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591270"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: методы P/Invoke не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1401: P / Invokes не должны быть видимыми](https://docs.microsoft.com/visualstudio/code-quality/ca1401-p-invokes-should-not-be-visible).

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут (также реализуется `Declare` ключевое слово в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Описание правила
 Методы, помеченные атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute> атрибут (или методы, определенные с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) использовать службы вызова платформы для доступа к неуправляемому коду. Такие методы не следует делать видимыми. Сохраняя эти методы закрытым или внутренним, вы убедитесь, что библиотека не может использоваться для нарушения безопасности, позволяя вызывающим объектам доступ к неуправляемым API, которые в противном случае они не отвечает.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените уровень доступа для метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере объявляется метод, который нарушает это правило.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]



