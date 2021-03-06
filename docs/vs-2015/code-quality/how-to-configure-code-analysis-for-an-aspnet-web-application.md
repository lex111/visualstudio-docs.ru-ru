---
title: 'Практическое: Настройка анализа кода для веб-приложения ASP.NET | Документация Майкрософт'
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
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b611e303c61e7be9586d6d746e5c859c8dbb5b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561841"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Практическое руководство. Настройка анализа кода для веб-приложения ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Настройка анализа кода для веб-приложения ASP.NET](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application).  
  
В [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] и [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] можно выбрать из списка анализа кода *наборов правил* для применения к [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] веб-приложения. Набор правил по умолчанию — Microsoft минимальные правила. Вы можете выбрать другое правило, применяется для веб-сайта.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Настройка набора правил для проекта платформы веб-страниц ASP.NET  
  
1.  Выберите веб-сайт в **обозревателе решений**.  
  
2.  На **анализ** меню, щелкните **Настройка анализа кода для веб-сайта**.  
  
3.  Если выбрано решение, и решение имеет более одного проекта, выберите сборки конфигурации и платформы операционной системы из **конфигурации** и **платформы** перечислены.  
  
4.  Для каждого проекта в решении, нажмите кнопку **набора правил** столбца и выберите имя правила, набора для запуска.  
  
5.  По умолчанию анализ кода запускается на всех проектов в решении. Чтобы отключить или включить анализ кода для конкретного проекта, выполните следующие действия:  
  
    1.  Щелкните правой кнопкой мыши имя проекта и выберите пункт Свойства.  
  
    2.  Установите или снимите флажок **включить анализ кода** "флажок". Можно также выполнить анализ кода вручную, выбрав **выполнить анализ кода на веб-сайте** из **анализ** меню.  
  
6.  В **выполнить этот набор правил** выберите в раскрывающемся списке, выполните следующие действия:  
  
    -   Выберите набор правил, который вы хотите использовать.  
  
    -   Выберите  **\<Обзор >** чтобы указать существующий настраиваемый набор правил, если его нет в списке.  
  
    -   Определите настраиваемый набор правил. Дополнительные сведения см. в разделе [Создание настраиваемых наборов правил](../code-quality/creating-custom-code-analysis-rule-sets.md).



