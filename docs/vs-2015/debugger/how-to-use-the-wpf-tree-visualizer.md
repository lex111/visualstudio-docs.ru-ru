---
title: 'Практическое: использование визуализатора дерева WPF | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e99bdaac9feb343c594e808433d686e5d607b45
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592828"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Практическое руководство. Использование визуализатора дерева WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: использование визуализатора дерева WPF](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-wpf-tree-visualizer).  
  
Визуализатор дерева WPF можно использовать для изучения визуального дерева объекта WPF, а также для просмотра свойств зависимостей WPF для объектов, содержащихся в дереве. Дополнительные сведения о визуальных деревьях см. в разделе [деревья в WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Дополнительные сведения о свойствах зависимостей см. в разделе [Общие сведения о свойствах зависимостей](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 При открытии визуализатора дерева WPF отобразятся две панели: **визуального дерева** в левой части и **свойства** _имя_**:**  _Тип_ на правой панели. Выберите любой объект в **визуального дерева** области и **свойства** _имя_**:**_тип_ область автоматически обновляется для отображения свойств для этого объекта.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Открытие визуализатора дерева WPF  
  
1.  В подсказке **Watch** окне **"Видимые"** окна, или **"Локальные"** , рядом с именем объекта WPF щелкните стрелку возле значка лупы.  
  
     Откроется список визуализаторов.  
  
2.  Нажмите кнопку **визуализатора дерева WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Поиск в визуальном дереве  
  
-   В **визуального дерева** области, введите строку для поиска в **поиска** поле.  
  
     Визуализатор дерева WPF немедленно найдет первый объект визуального дерева, соответствующий введенной строке. Для поиска более точных совпадений введите больше символов.  
  
    -   Чтобы перейти к следующему совпадению, в пределах визуального дерева, щелкните **Далее**.  
  
    -   Чтобы вернуться к предыдущему совпадению, нажмите кнопку **Prev**.  
  
    -   Чтобы очистить условия поиска, нажмите кнопку **снимите**.  
  
### <a name="to-search-the-properties-list"></a>Поиск в списке свойств  
  
-   В **свойства** _имя_**:**_тип_ области, введите строку, которую необходимо найти в **фильтрации**поле.  
  
     Визуализатор дерева WPF немедленно найдет свойства, соответствующие введенной строке; после этого появится список тех свойств, которые совпадают с введенной строкой. Для поиска более точных совпадений введите больше символов.  
  
    -   Чтобы очистить условия поиска, нажмите кнопку **снимите**.  
  
### <a name="to-close-the-visualizer"></a>Закрытие визуализатора  
  
-   Нажмите кнопку **закрыть** значок в правом верхнем углу диалогового окна.  
  
## <a name="see-also"></a>См. также  
 [Практическое: использование визуализатора](../misc/how-to-use-a-visualizer.md)   
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Деревья в WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Общие сведения о свойствах зависимости](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)



