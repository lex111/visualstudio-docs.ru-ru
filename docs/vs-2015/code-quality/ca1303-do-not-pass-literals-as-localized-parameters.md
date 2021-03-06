---
title: 'CA1303: Не следует передавать литералы в локализованных параметров | Документация Майкрософт'
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
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fcb7f9f4cd57f287ec7a2bab900a78d21f23846
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591264"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: не следует передавать литералы в виде локализованных параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1303: не следует передавать литералы в локализованных параметров](https://docs.microsoft.com/visualstudio/code-quality/ca1303-do-not-pass-literals-as-localized-parameters).

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод передает строковый литерал в качестве параметра конструктору или методу в [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] классов библиотеки и строка должна быть локализуемой.

 Это предупреждение возникает в том случае, если строковый литерал передается как значение параметра или свойства, а также один или несколько из следующих условий верно:

-   <xref:System.ComponentModel.LocalizableAttribute> Установлен атрибут параметра или свойства в значение true.

-   Имя параметра или свойства содержит «Text», «Message» или «Заголовок».

-   Строковый параметр, который передается методу Console.Write и Console.WriteLine называется «value» или «format».

## <a name="rule-description"></a>Описание правила
 Строковые литералы, внедренные в исходный код, сложно локализировать.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените строковый литерал строки, полученной через экземпляр <xref:System.Resources.ResourceManager> класса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если библиотека кода не будет локализовано, или в том случае, если строка не предоставляется конечному пользователю или разработчик, использующий библиотеку кода.

 Пользователи могут избавиться от методов, которые не должны передаваться локализованные строки, переименовав параметр или свойство с именем, или помечая эти элементы как условные помех.

## <a name="example"></a>Пример
 В следующем примере метод, который создает исключение, если любой из двух аргументов выходят за пределы диапазона. Для первого аргумента конструктору исключения передается строковый литерал, который нарушает это правило. Для второго аргумента конструктора правильно передается строка извлечь с помощью <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>См. также
 [Ресурсы в приложениях для настольных систем](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



