---
title: 'CA1821: Удаляйте пустые методы завершения | Документация Майкрософт'
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
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8abb9f00e61c8c24e91921519c706356b6ded16c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591717"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: удаляйте пустые методы завершения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1821: удаляйте пустые методы завершения](https://docs.microsoft.com/visualstudio/code-quality/ca1821-remove-empty-finalizers).

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип реализует метод завершения, который является пустым, вызывает только метод завершения базового типа или вызывает только условно создаваемые методы.

## <a name="rule-description"></a>Описание правила
 Если возможно, старайтесь не использовать финализаторы, поскольку из-за отслеживания жизненного срока объектов снижается производительность программы. Сборщик мусора будет выполняться метод завершения, прежде чем он собирает объекта. Это означает, что две коллекции требуется для сбора объекта. Пустой метод завершения влечет за собой дополнительных издержек без каких-либо преимуществ.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите пустой метод завершения. Если метод завершения не требуется для отладки, заключите весь метод завершения подобным `#if DEBUG / #endif` директивы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение из этого правила. Неотключенные снижает производительность и не дает преимуществ.

## <a name="example"></a>Пример
 В следующем примере показано пустой метод завершения, который должен быть удален, метод завершения, который должен быть заключен в `#if DEBUG / #endif` директивы и метод завершения, который использует `#if DEBUG / #endif` директивы правильно.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]



