---
title: Практическое руководство. Переключение между записью члена и записью ассоциации (конструктор классов) | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0659d024f74f154811c51248d523b8826824431f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562790"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Практическое руководство. Переключение между представлением в виде членов класса и представлением в виде ассоциации (конструктор классов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: изменение между представлением в виде членов и представлением в виде ассоциации (конструктор классов)](https://docs.microsoft.com/visualstudio/ide/how-to-change-between-member-notation-and-association-notation-class-designer).  
  
В конструкторе классов можно изменить способ представления не схеме классов отношения связи между двумя типами из записи члена с записью ассоциации, и наоборот. Члены отображаются в виде линий связи и часто дают более наглядное представление взаимосвязи типов.  
  
> [!NOTE]
>  Отношения ассоциаций могут быть представлены в виде свойства или поля члена. Чтобы изменить запись члена на запись ассоциации, один тип должен иметь член другого типа. Чтобы изменить запись ассоциации на запись члена, два типа должны быть соединены линией связи. Дополнительные сведения см. в разделе [Практическое руководство. Создание ассоциаций между типами (конструктор классов)](../ide/how-to-create-associations-between-types-class-designer.md). Если проект содержит несколько схем классов, изменения, внесенные в способ отображения отношений ассоциации, затронут только данную схему. Чтобы изменить способ отображения отношений ассоциации на другой схеме, откройте или выведите эту схему и выполните следующие действия.  
  
### <a name="to-change-member-notation-to-association-notation"></a>Чтобы изменить запись члена на запись ассоциации  
  
1.  В обозревателе решений в узле проекта откройте файл схемы классов (CD-файл).  
  
2.  В фигуре типа на схеме классов щелкните правой кнопкой мыши свойство члена или поле, представляющее связь, и выберите **Показывать как ассоциацию**.  
  
    > [!TIP]
    >  Если свойства или поля не отображаются в фигуре типа, возможно, секции в фигуре свернуты. Чтобы развернуть фигуру типа, дважды щелкните название секции либо щелкните правой кнопкой мыши фигуру типа и выберите **Развернуть**.  
  
     Член исчезнет из секции в фигуре типа, и появится линия связи, соединяющая два типа. Линия связи имеет метку с именем свойства или поля.  
  
### <a name="to-change-association-notation-to-member-notation"></a>Чтобы изменить запись ассоциации на запись члена  
  
-   На схеме классов щелкните правой кнопкой мыши линию связи и выберите **Показывать как свойство** или **Показывать как поле**.  
  
     Линия связи исчезнет, и свойство отобразится в соответствующей секции в фигуре типа на схеме.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание наследования между типами (конструктор классов)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Практическое руководство. Просмотр отношения наследования между типами (конструктор классов)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Просмотр типов и отношений (конструктор классов)](../ide/viewing-types-and-relationships-class-designer.md)   
 [Практическое руководство. Визуализация ассоциации коллекции в конструкторе класса (конструктор классов)](../ide/how-to-visualize-a-collection-association-class-designer.md)



