---
title: Обновление элементов проекта | Документация Майкрософт
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
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: 10005b38f01c3cad97cf8c7aab391e4546737295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571299"
---
# <a name="upgrading-project-items"></a>Обновление элементов проекта
При добавлении или управлять элементами внутри системы проектов, которые не реализуют, может потребоваться принять участие в процессе обновления проекта. Crystal Reports является примером элемента, который можно добавить в систему проектов.  
  
 Как правило реализации элемента проекта нужно использовать уже полностью созданным экземпляром и обновленного проекта, так как им нужно знать, какие ссылки на проект и какие другие свойства проекта есть для принятия решения об обновлении.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Чтобы получить уведомление об обновлении проекта  
  
1.  Задайте <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> флаг (определенных в файле vsshell80.idl) в реализации элемента проекта. В результате элемент проекта VSPackage автоматически загрузку при [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] оболочки определяет, что система проектов находится в процессе обновления.  
  
2.  Уведомить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> метод.  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Интерфейс срабатывает после реализации системы проекта завершении обновления и создается новый обновленный проект. В зависимости от сценария <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс срабатывает после <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> методы.  
  
### <a name="to-upgrade-the-project-item-files"></a>Чтобы обновить файлы элементов проекта  
  
1.  Необходимо тщательно управлять процесс резервного копирования файла в реализации элемента проекта. Это относится, в частности, для резервного копирования side-by-side, где `fUpgradeFlag` параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> задан метод <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, куда помещаются файлы, которые созданы резервные копии вдоль стороны файлы, которые обозначены как «расширения» OLD. Старше системное время, когда проект был обновлен файла резервной копии может быть назначен как устаревший. Кроме того они могут быть перезаписаны, если только вы выполнить определенные действия, чтобы избежать этого.  
  
2.  Во время вашего элемента проекта получает уведомление о обновления проекта, **мастера преобразования Visual Studio** по-прежнему отображается. Таким образом, следует использовать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> интерфейс для предоставления сообщений обновления пользовательского интерфейса мастера.  
  
## <a name="see-also"></a>См. также  
 [Мастер преобразования Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Обновление пользовательских проектов](../misc/upgrading-custom-projects.md)