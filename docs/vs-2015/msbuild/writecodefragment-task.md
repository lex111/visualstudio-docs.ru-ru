---
title: Задача WriteCodeFragment | Документы Майкрософт
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
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95780e4de5a14d18b755908e06bc990e90d805aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572212"
---
# <a name="writecodefragment-task"></a>Задача WriteCodeFragment
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача WriteCodeFragment](https://docs.microsoft.com/visualstudio/msbuild/writecodefragment-task).  
  
  
Создает временный файл кода из указанного созданного фрагмента кода. Не удаляет этот файл.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `WriteCodeFragment` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AssemblyAttributes`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Описание атрибутов для записи. Значение элемента `Include` представляет собой полное имя типа атрибута, например "System.AssemblyVersionAttribute".<br /><br /> Каждый элемент метаданных является парой имя-значение для параметра, который должен иметь тип `String`. Некоторые атрибуты допускают только позиционные аргументы конструктора. Однако подобные аргументы можно использовать в любом атрибуте. Чтобы задать позиционные атрибуты конструктора, используйте имена метаданных, похожие на "_Parameter1", "_Parameter2" и т. д.<br /><br /> Индекс параметра невозможно пропустить.|  
|`Language`|Обязательный параметр `String` .<br /><br /> Задает язык для создаваемого кода.<br /><br /> `Language` может быть любым языком, для которого доступен поставщик CodeDom, например "C#" или "VisualBasic". Выдаваемый файл будет иметь стандартное расширение имени для этого языка.|  
|`OutputDirectory`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает папку назначения для созданного кода, которая обычно является промежуточной.|  
|`OutputFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает путь к созданному файлу. Если этот параметр задан с помощью имени файла, папка назначения добавляется в начало этого имени. Если он задан с помощью корневой папки, папка назначения игнорируется.<br /><br /> Если этот параметр не задан, имя выходного файла состоит из папки назначения, произвольного имени файла и стандартного расширения для указанного языка.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



