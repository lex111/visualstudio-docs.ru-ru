---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dc3a9000056babd5a05577dfa95af42a824f538
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557796"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [-обновление (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/upgrade-devenv-exe).  
  
  
Обновляет файл решения и все его файлы проектов либо указанный файл проекта до текущих форматов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для этих файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Аргументы  
 `SolutionFile`  
 Требуется при обновлении всего решения и его проектов. Путь и имя для файла решения Можно ввести только имя файла решения или полный путь и имя файла решения. Если папка или файл еще не существуют, они будут созданы.  
  
 `ProjectFile`  
 Требуется при обновлении одного проекта. Путь и имя для файла проекта в решении. Можно ввести только имя файла проекта или полный путь и имя файла проекта. Если папка или файл еще не существуют, они будут созданы.  
  
## <a name="remarks"></a>Примечания  
 Резервные копии автоматически создаются и копируются в каталог с именем Backup, который создается в текущем каталоге.  
  
 Решения или проекты в системе управления версиями необходимо получать для изменения, прежде чем их можно будет обновить.  
  
 Использование параметра `/upgrade` не приводит к запуску [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Результаты обновления можно просмотреть в отчете об обновлении для языка разработки конкретного решения или проекта. Сведения об ошибках или использовании не возвращаются. Дополнительные сведения об обновлении проектов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], см. в разделе [как: Устранение неполадок с неудачной Visual Studio проект обновления](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## <a name="example"></a>Пример  
 В этом примере выполняется обновление файла решения с именем MyProject.sln в папке по умолчанию для решений [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>См. также  
 [Практическое: Устранение неполадок с неудачными обновлениями Visual Studio проекта](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



