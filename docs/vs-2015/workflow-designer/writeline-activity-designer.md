---
title: Конструктор действия WriteLine | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f1085c7a8989ebfdecdf0e9782afeeaf1e9b4400
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563935"
---
# <a name="writeline-activity-designer"></a>Конструктор действия WriteLine
**WriteLine** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.WriteLine> действия.  
  
## <a name="the-writeline-activity"></a>Операция WriteLine  
 Операция <xref:System.Activities.Statements.WriteLine> выполняет запись текста в указанный объект <xref:System.IO.TextWriter>. Если не указано <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> выполняет запись текста к консоли.  
  
### <a name="using-the-writeline-activity-designer"></a>Использование конструктора действий WriteLine  
 **WriteLine** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов**вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **WriteLine** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.WriteLine> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для WriteLine. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **WriteLine** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-writeline-properties"></a>Свойства WriteLine  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.WriteLine> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.WriteLine>. Значение по умолчанию WriteLine. Для значения <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего всегда использовать такое значение.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Текст для записи. Чтобы задать свойство, введите выражение Visual Basic в **текст** поле **WriteLine** действие конструктора или в сетке свойств.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Класс <xref:System.IO.TextWriter>, в который <xref:System.Activities.Statements.WriteLine> записывает <xref:System.Activities.Statements.WriteLine.Text%2A>. По умолчанию - консоль.|  
  
## <a name="see-also"></a>См. также  
 [Примитивы](../workflow-designer/primitives-activity-designers.md)   
 [назначить](../workflow-designer/assign-activity-designer.md)   
 [Задержка](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)