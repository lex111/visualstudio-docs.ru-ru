---
title: Пример расширения Excel. Класс PropertyProvider | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: d421f4f5b2f5fbdb2f78c6b72830ac8722e56aa2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571949"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Пример расширения Excel. Класс PropertyProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [пример расширения Excel: класс PropertyProvider](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-propertyprovider-class).  
  
Этот внутренний класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> и обеспечивает свойства для элементов [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], чтобы можно было записывать и воспроизводить тесты пользовательского интерфейса.  
  
## <a name="getcontrolsupportlevel-method"></a>Метод GetControlSupportLevel  
 Метод <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> возвращает число, обозначающее уровень поддержки, обеспечиваемый поставщиком свойства для указанного элемента управления. Чем выше это значение, тем лучше поставщик свойств поддерживает элемент управления. В данном случае метод проверяет значение свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> указанного элемента управления. Если значение равняется Excel, а свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> задает `CellElement`, метод возвращает наибольшее значение; в противном случае он возвращает ноль, что означает, что поддержка не предоставляется.  
  
## <a name="getpropertynames-method"></a>Метод GetPropertyNames  
 Возвращает словарь имен и дескрипторов свойств для поддерживаемых свойств элемента управления "Ячейка" Excel.  
  
## <a name="getpropertydescriptor-method"></a>Метод GetPropertyDescriptor  
 Этот метод вызывается платформой тестирования для получения предварительно определенного дескриптора свойства для указанного имени свойства.  
  
## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Методы GetPropertyValue и SetPropertyValue  
 Метод `GetPropertyValue` использует класс `Communicator` этого расширения, чтобы возвращать значение свойства из Excel. Метод `SetPropertyValue` использует класс <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> и компонент `Communicator`, чтобы задавать значение свойства. Эти методы вызываются платформой тестирования.  
  
## <a name="code-generation-customization-methods"></a>Методы настройки создания кода  
 Для данного расширения эти методы не реализованы. Поэтому они возвращают значение `null` или вызывают исключение <xref:System.NotImplementedException>.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



