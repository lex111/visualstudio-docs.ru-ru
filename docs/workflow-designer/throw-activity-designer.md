---
title: Конструктор рабочих процессов - конструктор действия Throw
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71cf547a1ea3599de8926e40ca5a43f3bdea0f71
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758325"
---
# <a name="throw-activity-designer"></a>Конструктор действия Throw

**Throw** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Throw> действия.

## <a name="the-throw-activity"></a>Действие Throw

Действие <xref:System.Activities.Statements.Throw> вызывает исключение.

### <a name="using-the-throw-activity-designer"></a>Использование конструктора операций Throw

Доступ **Throw** конструктора действий в **обработка ошибок** категории **элементов**.

**Throw** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Throw> действие по умолчанию **DisplayName** для Throw. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Throw** конструктора действий или в **DisplayName** поле таблицы свойств. Свойство <xref:System.Activities.Statements.Throw.Exception%2A> должно редактироваться в таблице свойств.

### <a name="the-throw-properties"></a>Свойства Throw

В следующей таблице показаны свойства <xref:System.Activities.Statements.Throw> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Throw>. По умолчанию используется Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Вызываемое исключение. Данное исключение должно быть производным от класса <xref:System.Exception>. Чтобы указать исключение, введите выражение Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Конструктор действия Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)