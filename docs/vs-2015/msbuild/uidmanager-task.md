---
title: Задача UidManager | Документация Майкрософт
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
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f64a91ddf1eea2bdd74bd64e2d33acfd4d60827
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561381"
---
# <a name="uidmanager-task"></a>Задача UidManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача UidManager](https://docs.microsoft.com/visualstudio/msbuild/uidmanager-task).  
  
  
Задача <xref:Microsoft.Build.Tasks.Windows.UidManager> проверяет, обновляет или удаляет уникальные идентификаторы (UID) для локализации всех элементов [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)], включенных в исходные файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`IntermediateDirectory`|Необязательный параметр типа **String**.<br /><br /> Определяет каталог, используемый для резервного копирования файлов источника [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)], которые указываются с помощью параметра **MarkupFiles**.|  
|`MarkupFiles`|Обязательный параметр **ITaskItem[]**.<br /><br /> Определяет файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] источника, включаемые для проверки, обновления или удаления UID.|  
|`Task`|Обязательный параметр **string**.<br /><br /> Определяет задачу управления UID для выполнения. Допустимые параметры: **Check**, **Update** и **Remove**.|  
  
## <a name="example"></a>Пример  
 В следующем примере задача <xref:Microsoft.Build.Tasks.Windows.UidManager> используется для проверки того, что файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] указанного источника содержат элементы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] с соответствующими UID.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Практическое руководство. Локализация приложения](http://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)



