---
title: Файлы TARGETS в MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 02/24/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 835d6e80c650a18b3e595d1c6dc0c8bafd6b958a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080016"
---
# <a name="msbuild-targets-files"></a>Файлы TARGETS в MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] включает в себя несколько *TARGETS*-файлов, содержащих элементы, свойства, целевые объекты и задачи для обычных сценариев. Эти файлы автоматически импортируются в большинство файлов проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для упрощения обслуживания и повышения удобочитаемости.  

 Обычно проекты импортируют один или несколько *TARGETS*-файлов для определения своего процесса сборки. Например, проект [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], созданный [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], будет импортировать *Microsoft.CSharp.targets*, который импортирует *Microsoft.Common.targets*. Сам проект [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] будет определять элементы и свойства, относящиеся к данному проекту, а стандартные правила сборки для проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] определяются в импортированных *TARGETS*-файлах.  

 Значение `$(MSBuildToolsPath)` определяет путь к этим общим *TARGETS*-файлам. Если `ToolsVersion` имеет значение 4.0, файлы находятся в следующем расположении: *\<путь_установки_Windows>\Microsoft.NET\Framework\v4.0.30319\\*  

> [!NOTE]
>  Дополнительные сведения о создании собственных целевых объектов см. в разделе [Целевые объекты](../msbuild/msbuild-targets.md). Сведения об использовании элемента `Import` для вставки файла проекта в другой файл проекта см. в разделах [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md) и [Практическое руководство. Использование одного и того же целевого объекта в нескольких файлах проектов](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Общие файлы TARGETS  

|Файл *TARGETS*|Описание:|  
|-------------------|-----------------|  
|*Microsoft.Common.targets*|Определяет этапы стандартного процесса сборки для проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Импортированы с помощью файлов *Microsoft.CSharp.targets* и *Microsoft.VisualBasic.targets*, которые включают в себя следующий оператор: `<Import Project="Microsoft.Common.targets" />`|  
|*Microsoft.CSharp.targets*|Определяет этапы стандартного процесса сборки для проектов Visual C#.<br /><br /> Импортированы с помощью файлов проекта Visual C# (с расширением *CSPROJ*), которые включают в себя следующий оператор: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|*Microsoft.VisualBasic.targets*|Определяет этапы стандартного процесса сборки для проектов Visual Basic.<br /><br /> Импортированы с помощью файлов проекта Visual Basic (с расширением *VBPROJ*), которые включают в себя следующий оператор: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
*Directory.Build.targets* является определяемым пользователем файлом, который содержит настройки для проектов в каталоге. Этот файл автоматически импортируется из *Microsoft.Common.targets*, пока свойству **ImportDirectoryBuildTargets** не будет назначено значение **false**.

## <a name="see-also"></a>См. также  
 [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
