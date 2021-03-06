---
title: 'CA1500: Имена переменных не должны совпадать с именами полей | Документация Майкрософт'
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
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fc900de76f0ae31cb3dc770fec681c1b7bed8213
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557927"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: имена переменных не должны совпадать с именами полей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [CA1500: имена переменных не должны совпадать с именами полей](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|При возникновении на параметр, который имеет то же имя в качестве поля:<br /><br /> Не критическое, если поле и метод, который объявляет, что параметры не видны за пределами сборки, независимо от того, сделанные изменения.<br />-Критическое, если вы измените имя поля и могут быть видны за пределами сборки.<br />-Критическое, если изменить имя параметра и метод, который объявляет его видно за пределами сборки.<br /><br /> При нарушении в локальной переменной, которая имеет то же имя в качестве поля:<br /><br /> Не критическое, если поле не видны за пределами сборки, независимо от того, изменения, внесенные.<br />Не критическое, если вы измените имя локальной переменной и не изменяйте имя поля.<br />-Критическое, если изменить имя поля, и он может отображаться за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Метод экземпляра объявляет параметр или локальную переменную, имя которого совпадает с именем поля экземпляра объявляющего типа. Для перехвата локальные переменные, которые нарушают правила, протестированных сборки должны быть построены с помощью отладочную информацию и связанный PDB-файл должен быть доступен.  
  
## <a name="rule-description"></a>Описание правила  
 Если имя поля экземпляра совпадает с параметром или имя локальной переменной, поля экземпляра осуществляется с помощью `this` (`Me` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ключевое слово при использовании внутри тела метода. При обслуживании кода, это просто забыть это различие, предполагается, что параметр или локальная переменная ссылается на поле экземпляра, что приводит к ошибкам. Это значение равно true, особенно для длительных метод тела выражений.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, переименуйте параметр или переменная или поле.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает два нарушения данного правила.  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]

