---
title: 'Практическое: укажите дополнительный код сведения с помощью __analysis_assume | Документация Майкрософт'
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
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a08ca5a35d08f284062323f2e75648852debb7bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562965"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Практическое руководство. Добавление дополнительных сведений о коде с помощью __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: определение дополнительных сведений кода, с помощью __analysis_assume](https://docs.microsoft.com/visualstudio/code-quality/how-to-specify-additional-code-information-by-using-analysis-assume).  
  
Возможность создания подсказок для средства анализа кода для кода C/C++, который поможет в процессе анализа и снижают количество предупреждений. Для предоставления дополнительных сведений, используйте следующую функцию:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -любое выражение, которое предполагается, что имеют значение true.  
  
 Средство анализа кода предполагается, что условие, представленный с помощью выражения имеет значение true, если в точке, где отображается функция и сохраняет значение true, пока выражение будет изменено, например, путем присваивания переменной.  
  
> [!NOTE]
>  `__analysis_assume` не влияет на оптимизации кода. За пределами средства анализа кода `__analysis_assume` определяется как холостой.  
  
## <a name="example"></a>Пример  
 В следующем коде используется `__analysis_assume` для устранения предупреждения анализа кода [C6388](../code-quality/c6388.md):  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)



