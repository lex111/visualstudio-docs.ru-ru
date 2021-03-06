---
title: Справочные сведения о задачах MSBuild | Документация Майкрософт
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
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43b7b413d403f2b85cc5c8e792cbee19488f8f11
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557570"
---
# <a name="msbuild-task-reference"></a>Справочные сведения о задачах MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [справочные сведения о задачах MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-task-reference).  
  
  
Задачи содержат код, который выполняется в процессе сборки. Задачи в следующем списке входят в состав [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. После установки [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] станут доступны дополнительные задачи, используемые для создания проектов [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. Дополнительные сведения см. в статье [Задачи MSBuild, относящиеся к Visual C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Помимо параметров, перечисленных в подразделах этого раздела, у каждой задачи существуют следующие параметры:  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный параметр `String` .<br /><br /> Выражение `Boolean`, на основании которого механизм [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] определяет, будет ли выполняться эта задача. Сведения о поддерживаемых в [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] условиях см. в статье [об условиях MSBuild](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Необязательный параметр. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое задачи последующие задачи в элементе [Target](../msbuild/target-element-msbuild.md) и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи остальные задачи в элементе `Target` и сборке не выполняются, и считается, что возник сбой всего элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в статье [Практическое руководство. Игнорирование ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>В этом разделе  
 [Базовый класс Task](../msbuild/task-base-class.md)  
 Добавляет несколько параметров в задачи, производные от класса <xref:Microsoft.Build.Utilities.Task>.  
  
 [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md)  
 Добавляет несколько параметров в задачи, производные от класса <xref:Microsoft.Build.Tasks.TaskExtension>.  
  
 [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)  
 Добавляет несколько параметров в задачи, производные от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>.  
  
 [Задача AL (компоновщик сборок)](../msbuild/al-assembly-linker-task.md)  
 Создает сборку с манифестом из одного или нескольких файлов, являющихся модулями или файлами ресурсов.  
  
 [Задача AspNetCompiler](../msbuild/aspnetcompiler-task.md)  
 Создает оболочку для программы aspnet_compiler.exe, которая выполняет предварительную компиляцию приложений ASP.NET.  
  
 [Задача AssignCulture](../msbuild/assignculture-task.md)  
 Назначает элементам идентификаторы языка.  
  
 [Задача AssignProjectConfiguration](../msbuild/assignprojectconfiguration-task.md)  
 Принимает строки конфигурации списка и назначает их конкретным проектам.  
  
 [Задача AssignTargetPath](../msbuild/assigntargetpath-task.md)  
 Принимает список файлов и добавляет атрибуты `<TargetPath>`, если они еще не указаны.  
  
 [Задача CallTarget](../msbuild/calltarget-task.md)  
 Вызывает целевой объект в файле проекта.  
  
 [Задача CombinePath](../msbuild/combinepath-task.md)  
 Объединяет указанные пути в единый путь.  
  
 [Задача ConvertToAbsolutePath](../msbuild/converttoabsolutepath-task.md)  
 Преобразует относительный путь или ссылку в абсолютный путь.  
  
 [Задача Copy](../msbuild/copy-task.md)  
 Копирует файлы в новое расположение.  
  
 [Задача CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)  
 Создает имя манифеста в стиле [!INCLUDE[csprcs](../includes/csprcs-md.md)] на основе заданного имени RESX-файла или другого ресурса.  
  
 [Задача CreateItem](../msbuild/createitem-task.md)  
 Заполняет коллекции элементов входными элементами, позволяя копировать элементы из одного списка в другой.  
  
 [Задача CreateProperty](../msbuild/createproperty-task.md)  
 Заполняет свойства входными значениями, позволяя копировать значения из одного свойства или строки в другое свойство или строку.  
  
 [Задача CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Создает имя манифеста в стиле [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] на основе заданного имени RESX-файла или другого ресурса.  
  
 [Задача Csc](../msbuild/csc-task.md)  
 Вызывает компилятор Visual C# для создания исполняемых файлов, библиотек динамической компоновки или модулей кода.  
  
 [Задача Delete](../msbuild/delete-task.md)  
 Удаляет указанные файлы.  
  
 [Задача Error](../msbuild/error-task.md)  
 Останавливает сборку и регистрирует ошибку в журнале событий на основании вычисленного условного оператора.  
  
 [Задача Exec](../msbuild/exec-task.md)  
 Запускает заданную программу или команду с помощью заданных аргументов.  
  
 [Задача FindAppConfigFile](../msbuild/findappconfigfile-task.md)  
 Выполняет поиск файла app.config (если он имеется) в предоставленных списках.  
  
 [Задача FindInList](../msbuild/findinlist-task.md)  
 Выполняет поиск элемента с указанной спецификацией в заданном списке.  
  
 [Задача FindUnderPath](../msbuild/findunderpath-task.md)  
 Определяет, какие элементы в указанной коллекции находятся в указанной папке и ее подпапках.  
  
 [Задача FormatUrl](../msbuild/formaturl-task.md)  
 Преобразовывает URL-адрес в правильный формат URL-адреса.  
  
 [Задача FormatVersion](../msbuild/formatversion-task.md)  
 Добавляет номер редакции к номеру версии.  
  
 [Задача GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)  
 Создает манифест приложения [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] или собственный манифест.  
  
 [Задача GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)  
 Задача обеспечивает автоматическое обнаружение, скачивание и установку приложения и необходимых для него компонентов.  
  
 [Задача GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)  
 Создает манифест развертывания [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 [Задача GenerateResource](../msbuild/generateresource-task.md)  
 Преобразовывает TXT- и RESX-файлы в двоичные RESOURCES-файлы среды CLR.  
  
 [Задача GenerateTrustInfo](../msbuild/generatetrustinfo-task.md)  
 Создает доверие к приложению из базового манифеста и из параметров `TargetZone` и `ExcludedPermissions`.  
  
 [Задача GetAssemblyIdentity](../msbuild/getassemblyidentity-task.md)  
 Извлекает идентификаторы сборок из указанных файлов и выводит сведения об удостоверении.  
  
 [Задача GetFrameworkPath](../msbuild/getframeworkpath-task.md)  
 Извлекает путь к сборкам [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 [Задача GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)  
 Извлекает путь к [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
 [Задача GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)  
 Возвращает пути к эталонным сборкам для различных версий .NET Framework.  
  
 [Задача LC](../msbuild/lc-task.md)  
 Создает LICENSE-файл из LICX-файла.  
  
 [Задача MakeDir](../msbuild/makedir-task.md)  
 Создает каталоги и при необходимости любые родительские каталоги.  
  
 [Задача Message](../msbuild/message-task.md)  
 Записывает сообщения в журнал в процессе сборки.  
  
 [Задача Move](../msbuild/move-task.md)  
 Перемещает файлы в новое расположение.  
  
 [Задача MSBuild](../msbuild/msbuild-task.md)  
 Выполняет сборку проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] на основе другого проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 [Задача ReadLinesFromFile](../msbuild/readlinesfromfile-task.md)  
 Считывает список элементов из текстового файла.  
  
 [Задача RegisterAssembly](../msbuild/registerassembly-task.md)  
 Считывает метаданные из указанной сборки и добавляет в реестр необходимые записи.  
  
 [Задача RemoveDir](../msbuild/removedir-task.md)  
 Удаляет указанные каталоги и все содержащиеся в них файлы и подкаталоги.  
  
 [Задача RemoveDuplicates](../msbuild/removeduplicates-task.md)  
 Удаляет повторяющиеся элементы из указанной коллекции элементов.  
  
 [Задача RequiresFramework35SP1Assembly](../msbuild/requiresframework35sp1assembly-task.md)  
 Определяет, требуется ли для приложения платформа .NET Framework 3.5 SP1.  
  
 Задача ResGen  
 Является устаревшей. Используйте [задачу GenerateResource](../msbuild/generateresource-task.md) для преобразования TXT- и RESX-файлов в двоичные RESOURCES-файлы среды CLR и обратно.  
  
 [Задача ResolveAssemblyReference](../msbuild/resolveassemblyreference-task.md)  
 Определяет все сборки, которые зависят от указанных сборок.  
  
 [Задача ResolveComReference](../msbuild/resolvecomreference-task.md)  
 Принимает список из одного или нескольких имен библиотек типов или TLB-файлов и определяет местоположение этих библиотек типов на диске.  
  
 [Задача ResolveKeySource](../msbuild/resolvekeysource-task.md)  
 Определяет источник ключа строгого имени.  
  
 [Задача ResolveManifestFiles](../msbuild/resolvemanifestfiles-task.md)  
 Разрешает следующие элементы в процессе сборки в файлы для создания манифеста: элементы сборки, зависимости, вспомогательные элементы, содержимое, отладочные символы и документация.  
  
 [Задача ResolveNativeReference](../msbuild/resolvenativereference-task.md)  
 Разрешает машинные ссылки.  
  
 [Задача ResolveNonMSBuildProjectOutput](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Определяет выходные файлы для ссылок на проекты, не относящихся к MSBuild.  
  
 [Задача SGen](../msbuild/sgen-task.md)  
 Создает сборку сериализации XML для типов в указанной сборке.  
  
 [Задача SignFile](../msbuild/signfile-task.md)  
 Подписывает указанный файл с помощью заданного сертификата.  
  
 [Задача Touch](../msbuild/touch-task.md)  
 Задает время доступа и изменения файлов.  
  
 [Задача UnregisterAssembly](../msbuild/unregisterassembly-task.md)  
 Отменяет регистрацию указанных сборок для целей COM-взаимодействия.  
  
 [Задача UpdateManifest](../msbuild/updatemanifest-task.md)  
 Обновляет выбранные свойства в манифесте и выполняет повторное подписание.  
  
 [Задача Vbc](../msbuild/vbc-task.md)  
 Вызывает компилятор Visual Basic для создания исполняемых файлов, библиотек динамической компоновки или модулей кода.  
  
 [Задача Warning](../msbuild/warning-task.md)  
 Регистрирует в журнале предупреждение в процессе сборки на основе вычисленного условного оператора.  
  
 [Задача WriteCodeFragment](../msbuild/writecodefragment-task.md)  
 Создает временный файл кода с использованием созданного указанного фрагмента кода. Не удаляет этот файл.  
  
 [Задача WriteLinesToFile](../msbuild/writelinestofile-task.md)  
 Записывает указанные элементы в указанный текстовый файл.  
  
 [Задача XmlPeek](../msbuild/xmlpeek-task.md)  
 Возвращает из XML-файла значения, указанные в запросе XPath.  
  
 [Задача XmlPoke](../msbuild/xmlpoke-task.md)  
 Задает в XML-файле значения, указанные в запросе XPath.  
  
 [Задача XslTransformation](../msbuild/xsltransformation-task.md)  
 Преобразует входные данные XML с помощью *XSLT* или скомпилированного XSLT и выводит результат на устройство вывода или в выходной файл.  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Написание задач](../msbuild/task-writing.md)   
 [Задачи](../msbuild/msbuild-tasks.md)



