---
title: 'Практическое: использование встроенных цветных элементов | Документация Майкрософт'
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
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20ed9b5424363eceec8cf4c3c5275a3a937a7003
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558763"
---
# <a name="how-to-use-built-in-colorable-items"></a>Практическое: использование встроенных цветных элементов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Используйте встроенные цветные элементы](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-use-built-in-colorable-items).  
  
Прежде чем использовать встроенные цветные элементы, необходимо сначала сообщается в интегрированной среде разработки (IDE), вы не предоставляли собственных пользовательских цветных элементов, которые в данном случае было бы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> объектов. Для этого параметру реестра для языковой службы.  
  
### <a name="to-use-built-in-colorable-items"></a>Чтобы использовать встроенные цветные элементы  
  
1.  В разделе HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*служб \Languages\Language\\*название языка*, где *X.Y* — это версия [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и *название языка* — это имя языка, создайте значение записи реестра типа DWORD `RequestStockColors`.  
  
2.  Задайте `RequestStockColors` значение записи реестра значение 1.  
  
     После создания реестра операции, ваш палитры <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод можно использовать члены <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> перечисления, заполните массив атрибутов цвета для использования с помощью редактора.  
  
    > [!NOTE]
    >  Не устанавливайте этот параметр реестра, если вы предоставляете пользовательских цветных элементов. Дополнительные сведения см. в разделе [пользовательских цветных элементов](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>См. также  
 [Цветовая маркировка синтаксиса в специализированных редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация цветовой маркировки синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)   
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)

