---
title: Предоставление поддержки для конструкторов "Отменить" | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df387259ed7a8623ba176ba09d0ceb1bba66bc0b
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "46496081"
---
# <a name="supplying-undo-support-to-designers"></a>Предоставление поддержки команды отмены для конструкторов
Конструкторы, таких как редакторы, обычно требуется для поддержки отмены операций, таким образом, пользователи могут отменить их последние изменения, при изменении элемента кода.  
  
 Большинство конструкторов, реализованные в Visual Studio имеет возможность отмены изменений, автоматически предоставляемых средой.  
  
 Реализации конструктора, которым требуется, чтобы обеспечить поддержку функции отмены:  
  
-   Задать механизмы управления отменой, можно реализовать абстрактный базовый класс <xref:System.ComponentModel.Design.UndoEngine>  
  
-   Укажите сохраняемость и CodeDOM поддержка путем реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> классы.  
  
 Дополнительные сведения о создании дизайнеры, использующие [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], см. в разделе [расширение поддержки времени разработки](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет инфраструктуру отмены по умолчанию путем:  
  
-   Предоставляя отменить реализации управления посредством <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> и <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> классы.  
  
-   Указав сохраняемости и поддержка CodeDOM через значение по умолчанию <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> реализаций.  
  
## <a name="obtaining-undo-support-automatically"></a>Получение поддержки отмены автоматически  
 Любого конструктора, созданные в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] имеет возможность отмены изменений автоматического и полного if, конструкторе:  
  
-   Использует <xref:System.Windows.Forms.Control> на основе класса для пользовательского интерфейса.  
  
-   Использует стандартный код на основе модели CodeDOM поколения и система анализа для создания кода и сохранения.  
  
     Дополнительные сведения о работе с поддержкой Visual Studio CodeDOM см. в разделе [динамического источника Создание и компиляция кода](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Когда следует использовать явные конструктора отмены поддержки  
 Конструкторы необходимо указывать свои собственные механизмы управления отменой, если они используют графический пользовательский интерфейс, называется адаптер представления, отличной от предоставляемых <xref:System.Windows.Forms.Control>.  
  
 Примером этого может созданию продукта с существует веб-графический интерфейс, а не [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] на основе графического интерфейса.  
  
 В таком случае необходимо зарегистрировать этот адаптер представления с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с помощью <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>и обеспечивает управление явного отката.  
  
 Дизайнерам необходимо для предоставления CodeDOM и сохраняемости поддержки, если они не используют [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] модели создания кода в <xref:System.CodeDom> пространства имен.  
  
## <a name="undo-support-features-of-the-designer"></a>Отменить функции поддержки конструктора  
 Пакет SDK для среды предоставляет реализации по умолчанию интерфейсов, необходимых для обеспечения отмены поддержки, который может использоваться конструкторами неиспользование <xref:System.Windows.Forms.Control> основе классы для их пользовательские интерфейсы или стандартную модель CodeDOM и сохраняемость.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Класс является производным от [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> класса, используя реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> класса для управления операции отмены.  
  
 Visual Studio предоставляет следующие функции для отмены конструктора:  
  
-   Функциональные возможности связанный откат несколько конструкторов.  
  
-   Дочерние единицы в конструкторе можно взаимодействовать с их родительские элементы путем реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> на <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 Пакет SDK для среды обеспечивает поддержку CodeDOM и постоянного хранения, указав:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> как реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Объект <xref:System.ComponentModel.Design.IComponentChangeService> предоставляемые [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' узла разработки.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Использование функций пакета SDK среды для предоставления поддержки отмены  
 Чтобы получить возможность отмены изменений, объект, реализующий конструктор должен:  
  
-   Создайте и инициализируйте экземпляр <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> класса является допустимым <xref:System.IServiceProvider> реализации.  
  
-   Это <xref:System.IServiceProvider> класс должен предоставлять следующие службы:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Дизайнеры, использующие [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сериализации CodeDOM, можно использовать <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> в состав [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] его реализацию <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         В этом случае <xref:System.IServiceProvider> класс, предоставляемый для <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> конструктор должен возвращать этот объект как реализация <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> класса.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Конструкторы по умолчанию <xref:System.ComponentModel.Design.DesignSurface> предоставляемые [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] основном приложении разработки гарантированно имеет реализацию по умолчанию <xref:System.ComponentModel.Design.IComponentChangeService> класса.  
  
 Реализация конструкторов <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> механизм отмены действий на основе автоматически отслеживает изменения, если:  
  
-   Изменения свойств выполняются через <xref:System.ComponentModel.TypeDescriptor> объекта.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService> события создаются вручную в том случае, когда отменяемое изменение фиксируется.  
  
-   Изменения в конструкторе был создан в контексте <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   Конструктор выбирает для явного создания блоков отмены, с помощью стандартных отмены, предоставляемые реализацию <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> или Visual Studio реализация <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, который является производным от <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> , а также предоставляет реализация обоих <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Расширения поддержки времени разработки](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)