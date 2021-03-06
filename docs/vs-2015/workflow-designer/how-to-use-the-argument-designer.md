---
title: 'Практическое: использовать конструктор аргументов | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: eaff53dc04c0ad2367147ae91c7de756e5ca4366
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561911"
---
# <a name="how-to-use-the-argument-designer"></a>Как использовать конструктор аргументов
По сравнению с предыдущими версиями [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], конструктор аргументов упрощает передачу данных в действие и из действия. Конструктор нажав **аргументы** кнопку в левом нижнем углу поля визуальной разработки. Конструктор содержит список аргументов, которые появляются в табличной форме и могут быть отсортированы по каждому заголовку столбца, за исключением **значение по умолчанию** столбца. Каждый аргумент содержит имя, направление передачи свойства (IN, OUT или IN/OUT), тип и значение выражения по умолчанию (если такое существует). Имя и значение выражения по умолчанию представляют собой изменяемые текстовые поля, а тип и направление - раскрывающееся меню. [!INCLUDE[crabout](../includes/crabout-md.md)] аргументы, см. в разделе [переменных и аргументов](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).  
  
### <a name="to-create-a-new-argument"></a>Создание нового аргумента  
  
1.  Откройте решение рабочего процесса или действия в [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Откройте конструктор аргументов, нажав кнопку **аргументы** кнопку в левом нижнем углу поля визуальной разработки. Появится конструктор аргументов.  
  
3.  Щелкните пустую строку с меткой **создать аргумент**. Это добавит новую строку с помощью нового аргумента, используя следующие значения по умолчанию: argumentx для **имя** где x — целое число с начальным значением 1, которая автоматически увеличивается на единицу для создания имен уникальный аргумент **в**  для **направление**, и **строка** для **тип аргумента**. Значение не добавляется для **значение по умолчанию**. В процессе разработки рабочего процесса эти значения можно изменить в любое время.  
  
    > [!NOTE]
    >  Для удаления аргумента выберите его, щелкнув его и нажмите клавишу **удалить** ключ.  
  
## <a name="see-also"></a>См. также  
 [В конструкторе рабочих процессов](../workflow-designer/using-the-workflow-designer.md)   
 [Переменные и аргументы](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)