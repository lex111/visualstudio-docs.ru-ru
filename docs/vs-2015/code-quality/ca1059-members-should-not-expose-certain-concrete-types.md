---
title: 'CA1059: Члены не должны предоставлять определенные устойчивые типы | Документация Майкрософт'
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
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 073d55a9a5ae6caa573a2c3db282aaa5e5ea4e57
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591980"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: члены не должны предоставлять определенные устойчивые типы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1059: члены не должны предоставлять определенные устойчивые типы](https://docs.microsoft.com/visualstudio/code-quality/ca1059-members-should-not-expose-certain-concrete-types).

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешне видимый член является определенным устойчивым типом или предоставляет определенные устойчивые типы посредством одного из своих параметров или возвращаемого значения. В настоящее время это правило выдает сообщение раскрытия следующие конкретные типы:

-   Тип, производный от <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Устойчивый тип – это тип, который имеет полную реализацию и экземпляр которого можно создать. Чтобы разрешить широкого использования этого элемента, замените конкретный тип предложенным интерфейсом. Это позволяет члену принимать любой тип, реализующий интерфейс или использоваться там, где ожидается тип, реализующий интерфейс.

 Ниже перечислены целевых устойчивых типов и их предлагаемые замен.

|Конкретный тип|Замена|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> С помощью интерфейса отделяет член от реализации источника данных XML.|

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените конкретный тип предложенным интерфейсом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить сообщение из этого правила, если конкретные функции, обеспечиваемые конкретный тип является обязательным.

## <a name="related-rules"></a>Связанные правила
 [CA1011: попробуйте передать базовые типы в качестве параметров](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)



