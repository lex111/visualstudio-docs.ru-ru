---
title: Задача FindAppConfigFile | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f3bffd988f10f5f396e96c920a27369c708012a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559634"
---
# <a name="findappconfigfile-task"></a>Задача FindAppConfigFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [findappconfigfile-задача](https://docs.microsoft.com/visualstudio/msbuild/findappconfigfile-task).  
  
  
Выполняет поиск файла app.config (если он имеется) в предоставленных списках.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FindAppConfigFile` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AppConfigFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает первый соответствующий элемент в списке (при его наличии).|  
|`PrimaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает основной список для поиска.|  
|`SecondaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает дополнительный список для поиска.|  
|`TargetPath`|Обязательный параметр `String` .<br /><br /> Указывает значение для добавления в качестве метаданных.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



