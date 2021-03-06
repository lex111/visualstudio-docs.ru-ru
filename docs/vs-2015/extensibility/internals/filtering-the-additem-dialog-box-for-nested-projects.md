---
title: Фильтрация диалогового окна AddItem для вложенных проектов | Документация Майкрософт
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
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c007a2aa0895460f539acb50f49844f8ec158fa7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568871"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Фильтрация диалогового окна AddItem для вложенных проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [фильтрация диалогового окна AddItem для вложенных проектов](https://docs.microsoft.com/visualstudio/extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects).  
  
При отображении **AddItem** диалоговое окно для вложенного проекта в родительский проект можно контролировать, какие элементы отображаются в диалоговом окне.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Интерфейс позволяет фильтровать узлы, которые будут находиться в **AddItem** диалоговое окно. При отображении дочернему проекту **AddItem** диалоговом окне можно реализовать родительского `IVsFilterAddProjectItemDlg` интерфейс и фильтрация элементов, которые могут отображаться в проекте дочернего элемента.  
  
 Если проекты сгруппированы по функциям конкретного родительского проектов, вы можете реализовать `IVsFilterAddProjectItemDlg` при выборе пользователем **добавить элемент проекта** в контекстном меню во вложенном проекте. Реализация `IvsFilterAddProjectItemDlg displays` только проект элементы или файлы, относящиеся к этой группе. Элементы проекта для других групп, исключаются из диалоговом окне, даже если они хранятся в том же каталоге.  
  
 Когда пользователь открывает **AddItem** диалоговое окно для дочернего элемента, родительский проект реализация `IVsFilterAddProjectItemDlg` интерфейс называется.  
  
 `IVsFilterAddProjectItemDlg` Интерфейса также можно реализовать фильтрацию по категории. Дополнительные сведения см. в разделе [Добавление элементов, чтобы добавить новый элемент диалоговым окнам](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) и [регистрации проекта и шаблонов элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)

