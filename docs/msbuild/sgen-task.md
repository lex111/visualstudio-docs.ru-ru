---
title: Задача SGen | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ed195596715c044268b2b1fdf434d1fda20967c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150894"
---
# <a name="sgen-task"></a>SGen - задача
Создает сборку сериализации XML для типов в указанной сборке. Эта задача служит оболочкой для инструмента создания XML-сериализатора (*Sgen.exe*). Дополнительные сведения см. в статье [Инструмент создания XML-сериализатора (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `SGen` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`BuildAssemblyName`|Обязательный параметр `String` .<br /><br /> Сборка, для которой создается код сериализации.|  
|`BuildAssemblyPath`|Обязательный параметр `String` .<br /><br /> Путь к сборке, для которой создается код сериализации.|  
|`DelaySign`|Необязательный параметр `Boolean` .<br /><br /> Значение `true` предписывает создание полностью подписанной сборки. Значение `false` предписывает лишь поместить в сборку открытый ключ.<br /><br /> Этот параметр не оказывает никакого эффекта, если не используется вместе с параметром `KeyFile` или `KeyContainer`.|  
|`KeyContainer`|Необязательный параметр `String` .<br /><br /> Задает контейнер, хранящий пару ключей. При этом сборка будет подписана путем вставки открытого ключа в манифест сборки. Затем задача подпишет окончательную сборку с помощью закрытого ключа.|  
|`KeyFile`|Необязательный параметр `String` .<br /><br /> Указывает пару ключей или открытый ключ для подписи сборки. Компилятор вставляет открытый ключ в манифест сборки, а затем подписывает окончательную сборку закрытым ключом.|  
|`Platform`|Необязательный параметр `String` .<br /><br /> Возвращает или задает платформу компилятора, используемую для создания выходной сборки. Этот параметр может иметь значение `x86`, `x64` или `anycpu`. Значение по умолчанию — `anycpu`.|  
|`References`|Необязательный параметр `String[]` .<br /><br /> Задает сборки, на которые ссылаются типы, требующие XML-сериализации.|  
|`SdkToolsPath`|Необязательный параметр `String` .<br /><br /> Указывает путь к средствам пакета SDK, например *resgen.exe*.|  
|`SerializationAssembly`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит созданную сборку сериализации.|  
|`SerializationAssemblyName`|Необязательный параметр `String` .<br /><br /> Указывает имя созданной сборки сериализации.|  
|`ShouldGenerateSerializer`|Обязательный параметр `Boolean` .<br /><br /> Если он имеет значение `true`, задача SGen должна создать сборку сериализации.|  
|`Timeout`|Необязательный параметр `Int32` .<br /><br /> Задает промежуток времени в миллисекундах, после которого исполняемый файл задачи прекращается. Значение по умолчанию — `Int.MaxValue`. Оно указывает, что период ожидания отсутствует.|  
|`ToolPath`|Необязательный параметр `String` .<br /><br /> Указывает расположение, из которого задача загружает базовый исполняемый (*sgen.exe*). Если этот параметр не задан, задача использует путь установки пакета SDK, соответствующий версии платформы, на которой выполняется [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Types`|Необязательный параметр `String[]` .<br /><br /> Возвращает или задает список определенных типов, для которых создается код сериализации. SGen создает код сериализации только для указанных типов.|  
|`UseProxyTypes`|Обязательный параметр `Boolean` .<br /><br /> Если он имеет значение `true`, задача SGen создает код сериализации только для типов прокси веб-службы XML.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.ToolTask>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)