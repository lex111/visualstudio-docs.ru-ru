---
title: 'Ca1824: следует Помечать сборки атрибутом NeutralResourcesLanguageAttribute | Документация Майкрософт'
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
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d433208e9bb63d770feb00f7f659c9e469a0c4e9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591297"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: следует помечать сборки атрибутом NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ca1824 следует: помечать сборки атрибутом NeutralResourcesLanguageAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute).

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка содержит **ResX**-ресурса на основе, но не имеет <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> примененных к нему.

## <a name="rule-description"></a>Описание правила
 **NeutralResourcesLanguage** атрибут сообщает **ResourceManager** языка, который использовался для отображения для сборки ресурсов нейтрального языка и региональных параметров. При поиске ресурсов языка и региональных параметров, как нейтральный язык ресурсов, **ResourceManager** автоматически использует ресурсы, которые находятся в основную сборку. Это делается вместо поиска для вспомогательной сборке, которая содержит текущий язык интерфейса пользователя для текущего потока. При этом повышается эффективность поиска первого загружаемого ресурса и может сократиться рабочее множество.

## <a name="fixing-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке и указывает язык, ресурсы нейтрального языка и региональных параметров.

## <a name="specifying-the-language"></a>Выбор языка

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Чтобы задать язык ресурсов нейтрального языка и региональных параметров

1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства**.

2.  На панели навигации слева выберите **приложения**, а затем нажмите кнопку **сведения о сборке**.

3.  В **сведения о сборке** диалоговом окне выберите язык из **нейтральный язык** стрелку раскрывающегося списка.

4.  Нажмите кнопку **ОК**.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Допускается, чтобы подавить предупреждение из этого правила. Тем не менее может снизить производительность при запуске.



