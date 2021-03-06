---
title: Команда доступности | Документация Майкрософт
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
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9933975b005241e89444c47a96b80bf0e43bfbcb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573209"
---
# <a name="command-availability"></a>Доступность команд
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [доступность команд](https://docs.microsoft.com/visualstudio/extensibility/internals/command-availability).  
  
Контекст Visual Studio определяет, какие команды доступны. Контекст может меняться в зависимости от текущего проекта, текущий редактор, пакеты VSPackage, который загружаются и другие аспекты интегрированной среде разработки (IDE).  
  
## <a name="command-contexts"></a>Командных контекстов  
 Следующие команды контексты являются самыми распространенными.  
  
-   **Интегрированная среда разработки** всегда доступны команды, предоставляемые интегрированной среды разработки.  
  
-   **VSPackage** пакеты VSPackage можно определить, когда команды, чтобы отобразить или скрыть.  
  
-   **Проект** команды проекта отображаются только для текущего выбранного проекта.  
  
-   **Редактор** только один редактор могут быть активны одновременно. Команды из активного редактора доступны. Редактор тесно сотрудничает с языковой службой. Служба языка необходимо обработать его команды в контексте связанного редактора.  
  
-   **Тип файла** редактор можно загрузить более одного типа. Доступные команды могут меняться в зависимости от типа файла.  
  
-   **Активное окно** последнего активного документа окна задает контекст пользовательского интерфейса пользователя для сочетания клавиш. Тем не менее окно инструментов, которая содержит таблицу привязки ключей, похожий на внутренний веб-браузера можно также задать контекст пользовательского интерфейса. Для окон документов, с несколькими вкладками, такие как редактор HTML Каждая вкладка имеет другую команду контекст GUID. После регистрации окна инструментов, он всегда был доступен на **представление** меню.  
  
-   **Контекст пользовательского интерфейса** контекстов пользовательского интерфейса определяются по значениям <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> класса, например, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> при сборке решения или <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> когда отладчик активен. Несколько контекстов пользовательского интерфейса может быть активен в то же время.  
  
## <a name="defining-custom-context-guids"></a>Определение пользовательских контекстные GUID  
 Если контекст соответствующей команды, которые уже не определен идентификатор GUID, можно определить ее в VSPackage и затем запрограммировать его, чтобы быть активными или неактивными, чтобы управлять видимостью ваших команд.  
  
1.  Зарегистрируйте идентификаторы GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метод.  
  
2.  Получить состояние идентификатор GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод.  
  
3.  Включать идентификаторы GUID контекста и отключать путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метод.  
  
    > [!CAUTION]
    >  Убедитесь, что VSPackage не влияет на любого существующего контекста идентификаторы GUID, так как других пакетов VSPackage может зависеть от них.  
  
## <a name="see-also"></a>См. также  
 [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)   
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

