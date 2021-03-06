---
title: Задача Error | Документы Майкрософт
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
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a7579a448a113c51a58e492da6ea9e7e4ca9ede
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561429"
---
# <a name="error-task"></a>Задача Error
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Ошибка задачи](https://docs.microsoft.com/visualstudio/msbuild/error-task).  
  
  
Останавливает сборку и регистрирует ошибку в журнале событий на основании вычисленного условного оператора.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи `Error`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Code`|Необязательный параметр `String` .<br /><br /> Код ошибки для связи с ошибкой.|  
|`File`|Необязательный параметр `String` .<br /><br /> Имя файла, содержащего ошибку. Если имя файла не указано, используется файл, содержащий задачу Error.|  
|`HelpKeyword`|Необязательный параметр `String` .<br /><br /> Ключевое слово справки, связанное с ошибкой.|  
|`Text`|Необязательный параметр `String` .<br /><br /> Текст ошибки, регистрируемый в журнале [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], если результат вычисления параметра `Condition` оказывается равным `true`.|  
  
## <a name="remarks"></a>Примечания  
 Задача `Error` позволяет передавать текст ошибок в средства ведения журнала и останавливать выполнение сборки в проектах [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Если результат вычисления параметра `Condition` оказывается равным `true`, сборка останавливается, а ошибка регистрируется в журнале. Если параметр `Condition` не существует, ошибка регистрируется в журнале, а выполнение сборки останавливается. Дополнительные сведения о ведении журнала см. в разделе [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода проверяется, что установлены все обязательные свойства. Если это не так, проект инициирует событие ошибки и регистрирует в журнале значение параметра `Text` задачи `Error`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)



