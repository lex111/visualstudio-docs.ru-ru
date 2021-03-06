---
title: Элемент Output (MSBuild) | Документация Майкрософт
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
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26535408374f2617ff9eda3a36b803116d848ecc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570965"
---
# <a name="output-element-msbuild"></a>Элемент Output (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент Output (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/output-element-msbuild).  
  
  
Сохраняет выходные данные задачи в элементах и свойствах.  
  
 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`TaskParameter`|Обязательный атрибут.<br /><br /> Имя выходного параметра задачи.|  
|`PropertyName`|Должен быть задан атрибут `PropertyName` или `ItemName`.<br /><br /> Свойство, которое получает значение от выходного параметра задачи. Проект может ссылаться на это свойство, используя синтаксис `$(`*PropertyName*`)`. В качестве имени для этого свойства можно использовать новое имя свойства или имя, которое уже определено в проекте.<br /><br /> Этот атрибут нельзя использовать вместе с атрибутом `ItemName`.|  
|`ItemName`|Должен быть задан атрибут `PropertyName` или `ItemName`.<br /><br /> Элемент, получающий значение от выходного параметра задачи. Проект может ссылаться на этот элемент, используя синтаксис `@(`*ItemName*`)`. В качестве имени для этого элемента можно использовать новое имя элемента или имя, которое уже определено в проекте.<br /><br /> Этот атрибут нельзя использовать вместе с атрибутом `PropertyName`.|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Задача](../msbuild/task-element-msbuild.md)|Создает и выполняет экземпляр задачи [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="example"></a>Пример  
 В следующем примере кода представлен элемент `Csc`, выполняемый внутри элемента `Target`. Элементы и свойства, передаваемые в качестве параметров задачи, объявляются за пределами этого сегмента кода. Значение выходного параметра `OutputAssembly` сохраняется в элементе `FinalAssemblyName`, а значение выходного параметра `BuildSucceeded` сохраняется в свойстве `BuildWorked`. Дополнительные сведения см. в разделе [Задачи](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)



