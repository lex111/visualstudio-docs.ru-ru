---
title: Элемент CommandPlacement | Документация Майкрософт
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
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5e2ffe04e7c31bc134a2c99ee1fdff24e371e89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569188"
---
# <a name="commandplacement-element"></a>Элемент CommandPlacement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент CommandPlacement](https://docs.microsoft.com/visualstudio/extensibility/commandplacement-element).  
  
Элемент CommandPlacement включает кнопки, группы и меню, должны быть включены в более чем одной группе или меню. С помощью элемента CommandPlacement, у вас нет полностью переопределить эти элементы, чтобы изменить внешний вид пользовательского интерфейса.  
  
 Дополнительные сведения см. в разделе [группы кнопок для повторного использования создание](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательно. Идентификатор guid набора команд, как определено в [элемент Symbols](../extensibility/symbols-element.md).|  
|id|Обязательно. Идентификатор меню, группу или команду, чтобы поместить, как определено в `Symbols Element`.|  
|priority|Обязательно. Определяет визуальную позицию элемента в его родительском элементе.|  
|Условие|Необязательный. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Родительский|Обязательно. Меню или группы, на котором размещается элемент, чтобы разместить.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandPlacements](../extensibility/commandplacements-element.md)|Указывает группы элементов CommandPlacements и CommandPlacement.|  
  
## <a name="example"></a>Пример  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент CommandPlacements](../extensibility/commandplacements-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

