---
title: 'Практическое: Настройка анализа кода для проекта управляемого кода | Документация Майкрософт'
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
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 34c3088aee4089c69669eaa3af5a08a657553363
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572797"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Практическое руководство. Настройка анализа кода для проекта управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Настройка анализа кода для проекта управляемого кода](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-a-managed-code-project).  
  
В [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] и [!INCLUDE[vsPro](../includes/vspro-md.md)], можно выбрать из списка анализа кода *наборов правил* для применения к проекту управляемого кода. Набор правил по умолчанию — минимально рекомендуемые правила Майкрософт. Вы можете применить еще одно правило в проект или ко всем проектам в решении.  
  
> [!NOTE]
>  Сведения о том, как настроить набор правил для веб-приложений ASP.NET см. в разделе [как: Настройка анализа кода для веб-приложения ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Чтобы настроить набор правил для проекта .NET Framework  
  
1.  В **обозревателе решений**, щелкните проект.  
  
2.  На **анализ** меню, щелкните **Настройка анализа кода для** *имя_проекта*.  
  
3.  В **конфигурации** и **платформы** списки, выберите платформу, конфигурации и целевой сборки.  
  
4.  Чтобы запустить анализ кода при каждом построении проекта с помощью выбранной конфигурации, выберите **включить анализ кода в построении (определяет константу CODE_ANALYSIS)** "флажок". Можно также выполнить анализ кода вручную, открыв **анализ** меню и выбрав пункт **выполнить анализ кода в** *имя_проекта*.  
  
5.  По умолчанию функция анализа кода выдает предупреждения, связанные с кодом, автоматически созданным внешними средствами. Чтобы просмотреть предупреждения из созданного кода, снимите **подавлять результаты из созданного кода** "флажок".  
  
    > [!NOTE]
    >  Этот параметр не отключает ошибки и предупреждения из созданного кода, если ошибки и предупреждения появляются в формах и шаблонах. Вы можете просматривать и обслуживать исходный код для формы или шаблона.  
  
6.  В **выполнить этот набор правил** выполните одно из следующих:  
  
    -   Выберите набор правил, который вы хотите использовать.  
  
    -   Нажмите кнопку  **\<Обзор... >** чтобы указать существующий настраиваемый набор правил, если его нет в списке.  
  
    -   Определите настраиваемый набор правил.  
  
         Дополнительные сведения см. в разделе [Создание настраиваемых наборов правил](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Настройка и использование набора настраиваемых правил](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)



