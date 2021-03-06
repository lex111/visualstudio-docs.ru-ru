---
title: 'CA2243: Атрибут синтаксический анализ строковых литералов правильно | Документация Майкрософт'
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
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e1e90ccfefad3b73a950849643009a92f074d4f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47573540"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: синтаксический анализ строковых литералов атрибута должен осуществляться правильно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2243: синтаксический анализ строковых литералов атрибута должен правильно](https://docs.microsoft.com/visualstudio/code-quality/ca2243-attribute-string-literals-should-parse-correctly).

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Строкового литерала атрибута не правильно проанализировать URL-адрес, идентификатор GUID или версии.

## <a name="rule-description"></a>Описание правила
 Поскольку атрибуты являются производными от <xref:System.Attribute?displayProperty=fullName>и атрибуты используются во время компиляции, их конструкторы могут передаваться только константные значения. Параметры атрибутов, которые должны представлять URL-адреса, идентификаторы GUID и версии не могут быть типизированы как <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, и <xref:System.Version?displayProperty=fullName>, так как эти типы нельзя представить в виде константы. Вместо этого они должны быть представлены строками.

 Так как параметр вводится как строка, вполне возможно, что во время компиляции может быть передан параметр неправильного формата.

 Это правило использует именования эвристический алгоритм для поиска параметров, которые представляют универсальный код ресурса (URI), глобальный уникальный идентификатор (GUID) или версии и проверяет правильность переданному значению.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Замените строку параметра правильно сформированный URL-адрес, идентификатор GUID или версии.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если параметр не представляет URL-адрес, идентификатор GUID или версии.

## <a name="example"></a>Пример
 В следующем примере показан код для AssemblyFileVersionAttribute, которое нарушает это правило.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Запускается следующее правило:

-   Параметры, которые содержат «version» и не может быть приведено к System.Version.

-   Параметры, которые содержат «guid» и не может быть приведено к System.Guid.

-   Параметры, которые содержат «uri», «urn» или «url» и не поддается на System.Uri.

## <a name="see-also"></a>См. также
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)



