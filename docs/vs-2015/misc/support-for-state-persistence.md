---
title: Поддержка сохранение состояния | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: douge
ms.openlocfilehash: 23278842d3a4c7c7123e5e84a07014749873a6f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560546"
---
# <a name="support-for-state-persistence"></a>Поддержка сохранения состояния
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] могут поддерживать состояние таких объектов. Например решения и проекта свойства сохранены и восстановить из файлов решений и проектов. Параметры пользователя можно экспортировать и импортировать из файлов параметров.  
  
 Пакеты VSPackage, обычно полагаются на локальное хранилище, в системном реестре или в папке данных приложения для текущего пользователя или компьютера. Значения, которые требуют небольшой объем пространства для хранения, такие как Integer и String, обычно хранятся в системном реестре. Значения, которые требуют много места для хранения, такие как точечные рисунки, сохраняются в файле. Путь к файлу сам, сохраняемых в системном реестре. Механизм сохранения необходимо иметь разрешение на доступ к локальному хранилищу.  
  
## <a name="support-for-locating-local-storage"></a>Поддержка поиска локального хранилища  
 <xref:Microsoft.VisualStudio.Shell.Package> Класс обеспечивает поддержку для поиска сведений о состоянии в папке system реестра или приложения данных для текущего пользователя или компьютера.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Возвращает путь к корневой раздел реестра локального компьютера для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], например HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0Exp.  
  
 Корневой элемент локального реестра получается из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> службы. Если этот параметр недоступен, он извлекается из <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> атрибута пакета VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Возвращает путь текущего пользователя (на каждом компьютере) корневой раздел реестра для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], например HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp.  
  
 Корневой элемент локального реестра получается из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> службы. Если этот параметр недоступен, он извлекается из атрибута DefaultLocalRegistryRoot VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Возвращает путь к каталогу, который служит в качестве общего хранилища для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] данные для текущего перемещающегося пользователя, например, C:\Documents and Settings\\*YourAccountName*\Application Data\Microsoft\ VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Возвращает путь к каталогу, который служит в качестве общего хранилища для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] данные для текущим неперемещающимся пользователем, например, C:\Documents and Settings\\*YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>См. также  
 [Состояние VSPackage](../misc/vspackage-state.md)