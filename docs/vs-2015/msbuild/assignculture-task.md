---
title: Задача AssignCulture | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ee44937f48101454a00128405fb03ce4260de4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559448"
---
# <a name="assignculture-task"></a>Задача AssignCulture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача AssignCulture](https://docs.microsoft.com/visualstudio/msbuild/assignculture-task).  
  
  
Эта задача принимает список элементов, которые могут содержать допустимую строку идентификатора языка и региональных параметров .NET в составе имени файла, и создает элементы, которые имеют метаданные `Culture`, содержащие соответствующий идентификатор языка и региональных параметров. Например, имя файла Form1.fr-fr.resx содержит идентификатор языка и региональных параметров "fr-fr", поэтому эта задача выдает элемент с тем же именем файла и метаданными `Culture`, равными `fr-fr`. Задача также выдает список имен файлов, из которых удалено указание языка и региональных параметров.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `AssignCulture`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AssignedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список элементов, полученных в параметре `Files`, с записью метаданных `Culture`, добавленной для каждого элемента.<br /><br /> Если входящий элемент из параметра `Files` уже содержит запись метаданных `Culture`, используется исходная запись метаданных.<br /><br /> Задача назначает запись метаданных `Culture` только в том случае, если имя файла содержит допустимый идентификатор языка и региональных параметров. Идентификатор языка и региональных параметров должен находиться между двумя последними точками в имени файла.|  
|`AssignedFilesWithCulture`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит подмножество элементов из `AssignedFiles` параметра, у которых есть запись метаданных `Culture`.|  
|`AssignedFilesWithNoCulture`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит подмножество элементов из `AssignedFiles` параметра, у которых нет записи метаданных `Culture`.|  
|`CultureNeutralAssignedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит тот же список элементов, который создается в параметре `AssignedFiles`, за исключением того, что из имени файла удалено упоминание языка и региональных параметров.<br /><br /> Задача удаляет язык и региональные параметры из имени файла лишь в том случае, если это допустимый идентификатор.|  
|`Files`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает список файлов с внедренными именами языка и региональных параметров для назначения.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример выполняет задачу `AssignCulture` с коллекцией элементов `ResourceFiles`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 Следующая таблица описывает значение выходных элементов после выполнения этой задачи. Метаданные элемента представлены в скобках после соответствующего элемента.  
  
|Коллекция элементов|Описание|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (без дополнительных метаданных)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (без дополнительных метаданных)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`без дополнительных метаданных)|  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



