---
title: Установка Visual Studio версии Side-by-Side | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: ae67e83b2f1444c09129ed5242afac2c3939c954
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571749"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Установка Visual Studio версии Side-by-Side
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эту версию Visual Studio можно установить на компьютер, на котором уже установлена более ранняя версия. В случае сбоя установки можно с помощью [средства сбора данных журнала](http://go.microsoft.com/fwlink/?LinkId=262077) собрать информацию о сбоях, чтобы самостоятельно найти причины неполадок.  
  
> [!NOTE]
>  Мы рекомендуем установить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] версий в том порядке, в котором они были выпущены. Например, Visual Studio 2013 необходимо устанавливать до Visual Studio 2015.  
  
 Прежде чем устанавливать несколько версий среды на одном компьютере, следует учесть следующие условия:  
  
-   При использовании Visual Studio 2015 для открытия решения, которое было создано в [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], впоследствии можно открыть и изменить решение в более ранней версии, пока еще не реализованы никакие возможности, характерные для Visual Studio 2015.  
  
-   Если вы попытаетесь использовать Visual Studio 2015 для открытия решения, которое было создано в [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] или более ранней версии, может потребоваться изменить проекты и файлы, которые совместимы с Visual Studio 2015. Дополнительные сведения см. в разделе [порт, миграция и обновление проектов Visual Studio](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md) страницы.  
  
-   В случае удаления версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с компьютера, на котором установлено более одной версии, сопоставления файлов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] будут удалены для всех версий. Изменить сопоставления файлов можно с помощью **восстановить сопоставления файлов** кнопку **среды**, **Общие** странице [параметры](../ide/reference/general-environment-options-dialog-box.md) диалоговое окно.  
  
-   Visual Studio не обновляет расширения автоматически, так как не все расширения совместимы. Необходимо переустановить расширения из [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) или с помощью средств издателя программного обеспечения.  
  
## <a name="net-framework-versions-and-side-by-side-installations"></a>Версии платформы .NET Framework и установка нескольких версий на один компьютер  
  
-   В проектах Visual Basic, Visual C# и Visual F# параметр **Целевая рабочая среда** в **конструкторе проектов** используется для определения того, какая версию платформы .NET Framework используется в проекте. Для проекта C++ можно вручную изменить целевую платформу, изменив VCXPROJ-файл. Дополнительные сведения см. в разделе [совместимость версий](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).  
  
     При создании проекта можно указать целевую версию .NET Framework проекта в списке **.NET Framework** в диалоговом окне **Создание проекта** .  
  
     Сведения, относящиеся к конкретному языку, см. в соответствующем разделе следующей таблицы.  
  
    |Язык|Раздел|  
    |--------------|-----------|  
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C#|[Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F#|[Настройка проектов](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|  
    |C++|[Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|  
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Запуск приложения JScript в предыдущей версии среды CLR](http://msdn.microsoft.com/en-us/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## <a name="see-also"></a>См. также  
 [Установка Visual Studio](../install/install-visual-studio-2015.md) [перенос, миграция и обновление проектов Visual Studio](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md)   
 [Построение C/C++ изолированных приложений и сборок Side-by-side](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)   
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)