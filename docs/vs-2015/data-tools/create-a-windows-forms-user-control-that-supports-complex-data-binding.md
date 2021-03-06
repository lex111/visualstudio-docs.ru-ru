---
title: Создать пользовательский элемент управления Windows Forms, который поддерживает сложную привязку данных | Документация Майкрософт
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 27f8a0e7fca0f14ee784eddaeb30f4d734994dc9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569086"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Создать пользовательский элемент управления Windows Forms, который поддерживает сложную привязку данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [создать пользовательский элемент управления Windows Forms с привязкой данных](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding).  
  
  
При отображении данных на формах в приложениях Windows, можно выбрать существующие элементы управления из **элементов**, или можно создать пользовательские элементы управления, если вашему приложению требуется функциональность, которая недоступна в стандартных элементах управления. В этом пошаговом руководстве демонстрируется создание элемента управления, реализующего <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Элементы управления, реализующие <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, содержат свойство `DataSource` и `DataMember`, которое можно привязать к данным. Такие элементы управления похожи на <xref:System.Windows.Forms.DataGridView> или <xref:System.Windows.Forms.ListBox>.  
  
 Дополнительные сведения о создании элементов управления, см. в разделе [Разработка Windows Forms элементов управления во время разработки](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 При создании элементов управления для использования в сценариях привязки к данным необходимо реализовать один из следующих атрибутов привязки данных:  
  
|Использование атрибута привязки данных|  
|-----------------------------------|  
|Реализуйте <xref:System.ComponentModel.DefaultBindingPropertyAttribute> на простых элементах управления, таких как <xref:System.Windows.Forms.TextBox>, которые отображают отдельный столбец (или свойство) данных. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает простую привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Реализуйте <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.DataGridView>, которые отображают списки (или таблицы) данных. (Этот процесс описан в данном пошаговом руководстве.)|  
|Реализуйте <xref:System.ComponentModel.LookupBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.ComboBox>, которые отображают списки (или таблицы) данных, но также должны представлять отдельный столбец или отдельное свойство. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms с привязкой данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 В этом пошаговом руководстве создается сложный элемент управления, отображающий строки данных из таблицы. В данном примере используется таблица `Customers` из учебной базы данных "Борей". Сложный элемент управления отображает таблицу клиентов в <xref:System.Windows.Forms.DataGridView> в пользовательском элементе управления.  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
-   Создайте новый **приложения Windows**.  
  
-   Добавьте новый **пользовательский элемент управления** в проект.  
  
-   Визуальное проектирование пользовательского элемента управления.  
  
-   Реализация атрибута `ComplexBindingProperty`.  
  
-   Создание набора данных с помощью [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Задайте **клиентов** в таблицу [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) для использования нового сложного элемента управления.  
  
-   Добавьте новый элемент управления, перетащив его из **окна "Источники данных"** на **Form1**.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к примеру базы данных "Борей". Дополнительные сведения см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Создание приложения Windows  
 Первым шагом является создание **приложения Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1.  В Visual Studio из **файл** меню, создайте новый **проекта**.  
  
2.  Назовите проект **ComplexControlWalkthrough**.  
  
3.  Выберите **приложения Windows**и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [клиентских приложений](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **ComplexControlWalkthrough** проект создан и добавлен **обозревателе решений**.  
  
## <a name="add-a-user-control-to-the-project"></a>Добавьте в проект пользовательский элемент управления  
 Так как в этом пошаговом руководстве создается сложный и привязываемый к данным элемент управления из **пользовательский элемент управления**, необходимо добавить **пользовательский элемент управления** в проект элемент.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект  
  
1.  Из **проекта** меню, выберите **добавить пользовательский элемент управления**.  
  
2.  Тип **ComplexDataGridView** в **имя** области, а затем выберите **добавить**.  
  
     **ComplexDataGridView** элемент управления добавляется **обозревателе решений**и откроется в конструкторе.  
  
## <a name="design-the-complexdatagridview-control"></a>Порядок проектирования элемента управления ComplexDataGridView  
 Этот этап добавляет <xref:System.Windows.Forms.DataGridView> в пользовательский элемент управления.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Порядок проектирования элемента управления ComplexDataGridView  
  
-   Перетащите <xref:System.Windows.Forms.DataGridView> из **элементов** в область конструктора пользовательского элемента управления.  
  
## <a name="add-the-required-data-binding-attribute"></a>Добавьте необходимый атрибут привязки данных  
 Для сложных элементов управления, поддерживающих привязку к данным, можно реализовать <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Реализация атрибута ComplexBindingProperties  
  
1.  Коммутатор **ComplexDataGridView** элемента управления в представление кода. (На **представление** меню, выберите **кода**.)  
  
2.  Замените код в `ComplexDataGridView` следующим кодом:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  В меню **Построение** выберите пункт **Построить решение**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Создание источника данных из базы данных  
 Этот шаг использует **конфигурации источника данных** мастер для создания источника данных на основе `Customers` таблицы в базе данных Northwind. Для создания подключения необходимо иметь доступ к учебной базе данных "Борей". Сведения о настройке учебной базе данных Northwind, см. в разделе [Установка SQL Server образцы баз данных](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  В меню **Данные** выберите команду **Показать источники данных**.  
  
2.  В **источников данных** выберите **добавить новый источник данных** запустить **конфигурации источника данных** мастера.  
  
3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.  
  
4.  На **Выбор подключения базы данных** странице выполните одно из следующих:  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.  
  
5.  Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных и нажмите кнопку **Далее**.  
  
6.  На **сохранение подключения в файле конфигурации приложения** щелкните **Далее**.  
  
7.  На **Выбор объектов базы данных** странице, разверните узел **таблиц** узла.  
  
8.  Выберите `Customers` таблицы, а затем нажмите кнопку **Готово**.  
  
     **NorthwindDataSet** добавляется в проект и `Customers` таблица появится в **источников данных** окна.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Порядок настройки таблицы клиентов на использование элемента управления ComplexDataGridView  
 В рамках **источников данных** окно, можно задать элемент управления должен быть создан перед перетаскиванием элементов на форму.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Порядок настройки таблицы клиентов на привязку к элементу управления ComplexDataGridView  
  
1.  Откройте **Form1** в конструкторе.  
  
2.  Разверните **клиентов** узел в **источников данных** окна.  
  
3.  Щелкните стрелку раскрывающегося списка в **клиентов** узел и выберите **Настройка**.  
  
4.  Выберите **ComplexDataGridView** из списка **связанные элементы управления** в **параметры настройки пользовательского интерфейса данных** диалоговое окно.  
  
5.  Щелкните стрелку раскрывающегося списка в `Customers` таблицу и выберите **ComplexDataGridView** в списке элементов управления.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols в форму  
 Созданием элементов управления с привязкой к данным путем перетаскивания элементов из **источников данных** окна на форму.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Создание элементов управления с привязкой к данным на форме  
  
-   Перетащите главный **клиентов** узел из **источников данных** окна в форму. Убедитесь, что **ComplexDataGridView** управления используется для отображения данных таблицы.  
  
## <a name="running-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
-   Нажмите клавишу F5 для запуска приложения.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после создания элемента управления, поддерживающего привязку к данным. Некоторые типичные дальнейшие действия.  
  
-   Помещение пользовательских элементов управления в библиотеку элементов управления, чтобы их можно было повторно использовать в других приложениях.  
  
-   Создание элементов управления, поддерживающих сценарии поиска. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms с привязкой данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Задать для элемента управления создается при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Элементы управления Windows Forms](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

