---
title: Добавление каталогов в диалоговое окно нового проекта | Документация Майкрософт
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
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e22f0566ddde7bfd795bb01141deabbecd532a19
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571563"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Добавление каталогов в диалоговое окно "Создание проекта"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [добавления каталогов в диалоговое окно нового проекта](https://docs.microsoft.com/visualstudio/extensibility/internals/adding-directories-to-the-new-project-dialog-box).  
  
При создании новых типов проектов, вы также можете зарегистрировать новый каталог в **новый проект** диалоговое окно, чтобы отобразить их для использования в качестве шаблонов. В следующем примере объясняется, как зарегистрировать новый каталог, а также называется узлом. В примере шаблонов, предоставляемых VSPackage CLSID_Package регистрируются. В результате в левой части **новый проект** диалоговое окно предлагает добавленный узел с именем определяется Folder_Label_ResID ресурсов. Этот ресурс загружается из вспомогательной Библиотеки VSPackage.  
  
 **Папку** значение представляет GUID папки, в которой отображается узел Folder_Label_ResID. В примере, представляет идентификатор GUID **другие проекты** папку в **типы проектов** области **новый проект** диалоговое окно. Если **другие проекты** значение отсутствует, то она позиционируется на верхнем уровне.  
  
 Значение TemplatesDir указывает полный путь к каталогу, содержащему шаблоны проектов. Эти файлы могут быть VSZ-файлы или файлы типичный шаблон для клонирования.  
  
 Если указать TemplatesLocalizedSubDir, он должен быть идентификатор ресурса строки с именем в подкаталог TemplatesDir, содержащий локализованных шаблонов. Так как [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] загружает строковый ресурс из вспомогательной библиотеки DLL при наличии, каждой вспомогательной библиотеки DLL могут содержать разные подкаталог с именем. Значение SortPriority указывает приоритет сортировки.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов в диалоговое окно "Добавление новых элементов"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

