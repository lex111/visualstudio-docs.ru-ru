---
title: Устранение проблем, связанных с метриками кода | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2cadd72f23fee6b89804fdbe61b105ff36b89caf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571472"
---
# <a name="troubleshooting-code-metrics-issues"></a>Устранение неполадок, связанных с метриками кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Устранение неполадок с метриками кода](https://docs.microsoft.com/visualstudio/code-quality/troubleshooting-code-metrics-issues).  
  
Во время сбора метрик кода могут возникать некоторые из следующих проблем:  
  
-   [Изменения в вычислениях сложности кода Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Изменения в вычислениях сложности кода Visual Studio 2010  
 Для одной и той же функции метрика сложности кода, вычисленная в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], может отличаться от метрики, вычисленной в более ранних версиях [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], в указанных ниже ситуациях.  
  
-   Функция содержит один или несколько блоков catch. В предыдущих версиях [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] блоки catch не включались в вычисления. В [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] сложность каждого блока catch прибавляется к сложности функции.  
  
-   Функция содержит оператор switch (Select Case в VB). Различия в компиляторах между [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] и более ранними версиями могут приводить к созданию разного кода MSIL для некоторых операторов switch, в которых имеются случаи передачи управления.  
  
## <a name="see-also"></a>См. также  
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



