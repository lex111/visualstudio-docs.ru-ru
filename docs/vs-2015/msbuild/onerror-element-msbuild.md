---
title: Элемент OnError (MSBuild) | Документация Майкрософт
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
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 323aff310061cf62af7cac10ee266c15d24e6eae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572302"
---
# <a name="onerror-element-msbuild"></a>Элемент OnError (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент OnError (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/onerror-element-msbuild).  
  
  
Вызывает выполнение одного или нескольких целевых объектов, если атрибут `ContinueOnError` для задачи, завершившейся ошибкой, имеет значение `false`.  
  
 \<Project>  
 \<Target>  
 \<OnError>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Обязательный атрибут.<br /><br /> Целевые объекты, которые следует выполнить при сбое задачи. Если целевых объектов несколько, разделите их точкой с запятой. Если целевых объектов несколько, они выполняются в указанном порядке.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Целевой объект](../msbuild/target-element-msbuild.md)|Элемент контейнера для задач [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] выполняет элемент `OnError`, если любая из задач элемента `Target` при завершении имеет атрибут `ContinueOnError` со значением `ErrorAndStop` (или `false`). Если задача завершается с ошибкой, выполняются целевые объекты, заданные в атрибуте `ExecuteTargets`. Если целевой объект содержит несколько элементов `OnError`, в случае сбоя задачи все элементы `OnError` выполняются последовательно.  
  
 Дополнительные сведения об атрибуте `ContinueOnError` см. в разделе [Элемент Task (MSBuild)](../msbuild/task-element-msbuild.md). Дополнительные сведения о целевых объектах см. в статье [Целевые объекты](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода выполняет задачи `TaskOne` и `TaskTwo`. Если `TaskOne` завершается ошибкой, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] оценивает элемент `OnError` и выполняет целевой объект `OtherTarget`.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [Целевые объекты](../msbuild/msbuild-targets.md)



