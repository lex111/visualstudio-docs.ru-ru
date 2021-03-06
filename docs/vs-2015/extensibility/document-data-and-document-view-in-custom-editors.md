---
title: Данные документа и документа просмотра в специализированных редакторах | Документация Майкрософт
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
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6df543f832fa85ea6d74fc2846355fbf9deab912
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559573"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Данные документа и представление документа в специализированных редакторах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [данные документа и представление документа в редакторах Custom](https://docs.microsoft.com/visualstudio/extensibility/document-data-and-document-view-in-custom-editors).  
  
Специализированный редактор состоит из двух частей: объект данных документа и объект представления документа. Как предполагают их имена, объект данных документа представляет текстовые данные для отображения, а объект представления документа (или «view») представляет один или несколько периодов, в котором отображается объект данных документа.  
  
## <a name="document-data-object"></a>Объект данных документа  
 Объект данных документа — это представление данных текста в текстовом буфере. Это объект COM, который сохраняет текст документа и другие сведения, обрабатывает сохраняемости документа и включает несколько представлений данных. Дополнительные сведения см. в разделе .  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> и [документов Windows](../extensibility/internals/document-windows.md).  
  
 Пользовательские редакторы и конструкторы можно использовать <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта или свои собственные пользовательские буфера. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> соответствует упрощенное внедрение модели для стандартного редактора, поддерживает несколько представлений и предоставляет интерфейсы событий, которые используются для управления несколькими представлениями.  
  
## <a name="document-view-object"></a>Объект представления документа  
 Окно, отображающее код и другие текстовые сообщения, известен как документ представлении или представлении. При создании редактора, можно выбрать одно представление, в котором текст отображается в одном окне, или несколько представление, в котором текст отображается в более одного окна. Выбор зависит от приложения. Например если требуется side-by-side редактирования, выбирается несколько представления. Каждое представление, связанный с записью в интегрированной среды разработки (IDE) запуск таблицы документов (RDT). Представление windows относящиеся к проекту или <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта.  
  
 Если ваш редактор поддерживает несколько представлений объекта данных документа, то данные документа и объекты представления документа необходим отдельный. В противном случае они могут быть сгруппированы вместе. Дополнительные сведения см. в разделе [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
 Интегрированная среда разработки уведомляет представления о событиях (например, при закрытии решения, содержащего документа), сопоставляя идентификатор элемента (ItemID) для каждой записи в таблице выполняющихся документов. Дополнительные сведения об этом см. в разделе [таблице выполняющихся документов](../extensibility/internals/running-document-table.md).  
  
 Существует два варианта для создания представления для настраиваемого редактора. Один является модель активации на месте, где представление размещено в окне с помощью элемента управления ActiveX или объект данных документа. Второй — упрощенной моделью внедрения, где размещается представление [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> реализован для обработки команды "окно". Сведения о модели встроенной активации, см. в разделе [встроенной активации](../misc/in-place-activation.md). Сведения о упрощенной модели внедрения, см. в разделе [упрощенное внедрение](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>См. также  
 [Поддержка представления нескольких документов](../extensibility/supporting-multiple-document-views.md)   
 [Упрощенное внедрение](../extensibility/simplified-embedding.md)   
 [Практическое: вложение представлений в данные документа](../extensibility/how-to-attach-views-to-document-data.md)   
 [Управление контейнером блокировки документа](../extensibility/document-lock-holder-management.md)   
 [Представления одной и несколькими вкладками](../extensibility/single-and-multi-tab-views.md)   
 [Сохранение стандартного документа](../extensibility/internals/saving-a-standard-document.md)   
 [Сохранение и запуск таблицы документов](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Определение Откроется редактор с файлом в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Фабрики редактора](../extensibility/editor-factories.md)

