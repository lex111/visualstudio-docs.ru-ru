---
title: 'Практическое: инициируют события, когда редактор теряет фокус | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2462e41470b72c63f5c96a69d2776af2a640c372
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562055"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Практическое: инициируют события, когда редактор теряет фокус
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Fire события когда редактор теряет фокус](https://docs.microsoft.com/visualstudio/extensibility/how-to-fire-events-when-the-editor-loses-focus).  
  
Иногда бывает необходимо знать, когда редактор теряет фокус на рамку окна. Например может потребоваться для извлечения кода из окна кода после редакторе фокуса на нем. Следующая процедура описывает, как переходить для получения уведомлений о редакторе теряет фокус.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Чтобы активировать событие в ответ на редактор теряет фокус  
  
1.  Мониторинг событий выбора путем получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> объекта из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> и укажите его в ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> объекта.  
  
3.  При вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, искать `elementid==SEID_WindowFrame`.  
  
4.  Тест `varValueNew` параметр для двух целей:  
  
    1.  Фрейм окна, которую вы ищете.  
  
    2.  Точка, по которому программа теряет выделение для этой рамки окна.

