---
title: 'Практическое: создать условие декларативного правила (для прежних версий) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 59eebe93b5c11fa1b02dc9ae481d0658010e961b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561355"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Как создать условие декларативного правила (для прежних версий)
В этом разделе описывается объявление условия правила с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Условный оператор оценивает значение **True** или **False**. Условие декларативного правила-это условный оператор, который создается с помощью [правило условие диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) и хранятся в виде XML с рабочим процессом. Он может включать предикаты, которые сравнивают состояние рабочего процесса и булеву алгебру, в которой объединено множество предикатов.  
  
 Условия декларативного правила используются в следующих готовых действиях Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Для создания условия декларативного правила используется Редактор условий для правил  
  
1.  В действии **свойства** окно, нажмите кнопку **условие** свойство или **UntilCondition** свойство зависимости от действия.  
  
2.  Выберите **условие декларативного правила** из списка для свойства.  
  
3.  Разверните **условие** или **UntilCondition** свойство.  
  
4.  Нажмите кнопку **ConditionName** свойство.  
  
5.  Нажмите кнопку **ConditionName** многоточие **[...]**  открыть **выбрать условие** диалоговое окно.  
  
6.  Нажмите кнопку **новое условие** открыть **редактор условий для правил** диалоговое окно.  
  
7.  Введите выражение для условия в **условие** текстовое поле.  
  
     Сведения о создании выражений условия см. в разделе [правило условие диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  После завершения создания выражения условия нажмите кнопку **ОК** чтобы закрыть диалоговое окно и создать условие правила с назначенным именем.  
  
     **Выбрать условие** откроется диалоговое окно.  
  
     Сведения об использовании **выбрать условие** диалоговом окне см. в разделе [выберите условие диалоговое окно (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>См. также  
 [Действия рабочего процесса прежних версий](../workflow-designer/legacy-workflow-activities.md)   
 [Использование ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Использование действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Использование действия Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [С помощью While действия](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Диалоговое окно «Редактор условий для правил» (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Выберите диалоговое окно «условие» (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)