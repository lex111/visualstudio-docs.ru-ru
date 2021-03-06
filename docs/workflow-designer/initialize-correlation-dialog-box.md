---
title: Конструктор рабочих процессов - диалоговое окно инициализации корреляции
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3525eb8964ed603e40ba74f0c06b17b494390c7
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755844"
---
# <a name="initialize-correlation-dialog-box"></a>Диалоговое окно «Инициализация корреляции»

**Инициализация корреляции** диалоговое окно используется в конструкторе рабочих процессов для изменения <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойство <xref:System.ServiceModel.Activities.InitializeCorrelation> действия. Дополнительные сведения см. в разделе [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

В следующей таблице описаны элементы пользовательского интерфейса (UI) **инициализация корреляции** диалоговое окно:

|Элемент пользовательского интерфейса|Описание:|
|----------------|-----------------|
|**Корреляция**|Дескриптор корреляции <xref:System.ServiceModel.Activities.CorrelationHandle> для инициализации.|
|**Инициализировать на**|По ключу/паре значений, содержащих данные инициализации. Это значение соответствует <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойство. Например пары "допустимый ключ значение", раздел с именем «OrderID» связан с переменной с именем OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Вызов диалогового окна «Инициализация корреляции»

Нажмите кнопку **представление** на **InitializeCorrelation** действие конструктора или выберите <xref:System.ServiceModel.Activities.InitializeCorrelation> действия в конструкторе рабочих процессов. Щелкните кнопку с многоточием рядом с полем <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойства в сетке свойств.

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)