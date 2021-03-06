---
title: Как использовать один и тот же целевой объект в нескольких файлах проектов | Документация Майкрософт
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
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ece9041d03ee8a17a4f97f8aad3971e1181edf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561574"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Как использовать одинаковый целевой объект в нескольких файлах проектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: использовать одинаковый целевой объект в нескольких файлах проектов](https://docs.microsoft.com/visualstudio/msbuild/how-to-use-the-same-target-in-multiple-project-files).  
  
  
Если вы уже создали несколько файлов проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], вы могли заметить, что в разных файлах проекта вы иногда используете одни и те же задачи и целевые объекты. Чтобы не включать полное описание этих задач и целевых объектов в каждый файл проекта, вы можете сохранить целевой объект в отдельный файл проекта и импортировать этот проект во все проекты, которые должны использовать этот же целевой объект.  
  
## <a name="using-the-import-element"></a>Использование элемента Import  
 Элемент `Import` позволяет вставить один файл проекта в другой файл проекта. Импортируемый файл проекта должен быть допустимым файлом проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] и XML-документом правильного формата. Атрибут `Project` задает путь к импортированному файлу проекта. Дополнительные сведения об элементе `Import` в статье [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Процедура импорта проекта  
  
1.  Определите в файле проекта, из которого выполняется импорт, все свойства и элементы, которые требуются в качестве параметров для свойств и элементов, указанных в импортируемом проекте.  
  
2.  Для импорта проекта используйте элемент `Import`. Пример:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  После элемента `Import` определите все свойства и элементы, которые будут переопределять используемые по умолчанию определения свойств и объектов, включенные в импортируемый проект.  
  
## <a name="order-of-evaluation"></a>Порядок вычислений  
 Когда [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] достигает элемента `Import`, импортируемый проект фактически вставляется в проект, из которого выполняется импорт, прямо в точке расположения элемента `Import`. Таким образом, расположение элемента `Import` может влиять на значения свойств и элементов. Важно понимать, какие свойства и элементы задает импортируемый проект, и какие свойства и элементы он использует.  
  
 При сборке проекта сначала вычисляются все свойства, а затем элементы. Например, следующий XML-код определяет импортируемый файл проекта MyCommon.targets:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Следующий XML-код определяет проект MyApp.proj, который импортирует MyCommon.targets:  
  
```  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 При сборке проекта вы увидите следующее сообщение:  
  
 `Name="MyCommon"`  
  
 Так как проект импортируется после того, как в файле MyApp.proj определяется свойство `Name`, определение `Name` из файла MyCommon.targets переопределяет значение, указанное в файле MyApp.proj. Если же проект будет импортирован раньше, чем определяется свойство Name, при сборке появится следующее сообщение:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>При импорте проектов мы рекомендуем использовать следующий подход.  
  
1.  Определите в файле основного проекта все свойства и элементы, которые требуются в качестве параметров для свойств и элементов, указанных в импортируемом проекте.  
  
2.  Импортируйте проект.  
  
3.  Затем определите все свойства и элементы, которые будут переопределять используемые по умолчанию определения свойств и объектов, включенные в импортируемый проект.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан файл MyCommon.targets, который импортируется в проект из второго примера. Файл TARGETS использует в качестве параметров сборки значения свойств, указанные в проекте, из которого выполняется импорт.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода выполняется импорт файла MyCommon.targets.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Целевые объекты](../msbuild/msbuild-targets.md)



