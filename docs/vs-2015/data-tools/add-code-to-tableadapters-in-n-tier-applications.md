---
title: Добавление кода для объектов TableAdapter в многоуровневых приложениях | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd46596ff474a33be42b8c5118404845a39c2b7d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562963"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Добавление кода для объектов TableAdapter в n-уровневых приложениях
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [добавьте код для объектов TableAdapter в многоуровневых приложениях](https://docs.microsoft.com/visualstudio/data-tools/add-code-to-tableadapters-in-n-tier-applications).  
  
  
Вы можете расширить функциональные возможности `TableAdapter` , создав файл разделяемого класса для `TableAdapter` и добавления к нему кода (вместо добавления кода к *DatasetName*. Файл DataSet.Designer). Разделяемые классы позволяют коду для конкретного класса необходимо распределить между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) или [partial (тип)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
 Код, который определяет `TableAdapter` создается каждый раз при внесении изменений `TableAdapter` (в [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md)). Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию `TableAdapter`. Чтобы предотвратить удаление во время повторного формирования кода `TableAdapter`, добавьте код в файл разделяемого класса `TableAdapter`.  
  
 По умолчанию, после разделения набора данных и `TableAdapter` кода, результат — это отдельные файлы классов в каждом проекте. Исходный проект содержит файл с именем *DatasetName*. Designer.vb (или *DatasetName*. Designer.cs), содержащий `TableAdapter` кода. Проект, который определен в **проект Dataset** свойство имеет файл с именем *DatasetName*. DataSet.Designer.vb (или *DatasetName*. DataSet.Designer.cs), содержащий код набора данных.  
  
> [!NOTE]
>  При разделении наборов данных и `TableAdapter`s (задавая **проект DataSet** свойство), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
> [!NOTE]
>  [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md) предоставляет функциональность для создания <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> обработчики событий, когда требуется проверка. Дополнительные сведения см. в разделе [Добавление проверки в n уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Добавление пользовательского кода адаптера таблицы в n уровневого приложения  
  
1.  Найдите проект, содержащий XSD-файл ( [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Дважды щелкните **.xsd** файл, чтобы открыть [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Щелкните правой кнопкой мыши `TableAdapter` , необходимо добавить код, а затем выберите**Просмотр кода**.  
  
     Разделяемый класс создается и открывается в редакторе кода.  
  
4.  Добавьте код в объявление разделяемого класса.  
  
5.  В следующем примере показано место добавления кода к `CustomersTableAdapter` в `NorthwindDataSet`:  
  
    ```vb  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```csharp  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о данных в N-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)   
 [Добавление кода для наборов данных в n уровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [Адаптеры таблиц](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Общие сведения о компоненте TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Общие сведения о иерархическое обновление](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Создание приложений для работы с данными](../data-tools/creating-data-applications.md)

