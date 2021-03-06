---
title: 'CA2221: Методы завершения должны быть защищены | Документация Майкрософт'
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
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d4b90f49ff895d6f39914a5a2b3e07a515103f44
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591660"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: методы завершения должны быть защищены
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2221: методы завершения должны быть защищены](https://docs.microsoft.com/visualstudio/code-quality/ca2221-finalizers-should-be-protected).

|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип реализует метод завершения, который не содержит семейства (защищенный) доступ.

## <a name="rule-description"></a>Описание правила
 В методах завершения должен использоваться модификатор доступа из семейства. Это правило применяется компиляторами C#, Visual Basic и Visual C++.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените метод завершения, чтобы быть доступным из семейства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Это правило не может быть нарушено в любой высокоуровневый язык .NET; нарушения возникают при создании промежуточного языка.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>См. также
 [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



