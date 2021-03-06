---
title: Представление модели содержимого | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0f2e73749e76d4449acc2a3debbec6ba8de416dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570975"
---
# <a name="content-model-view"></a>Представление модели содержимого
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [представления модели содержимого](https://docs.microsoft.com/visualstudio/xml-tools/content-model-view).  
  
  
Представление модели содержимого предоставляет графическое представление сведений о локальных и глобальных узлах схемы и их компонентах, включая простые и сложные типы, элементы, группы моделей, атрибуты и группы атрибутов. XML-комментарии и инструкции по обработке нельзя просматривать в представлении модели содержимого. Представление модели содержимого содержит две панели: **рабочей области** панель, которая содержит список узлов в [рабочей области конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md)и рабочую область конструирования, где можно просмотреть схемы содержимого модели узлы, выбранные в **рабочей области** панели. Представление модели содержимого также включает панель инструментов конструктора XML-схем и строку навигатора.  
  
 На следующем рисунке панель рабочей области содержит шесть узлов схемы. Узел `purchaseOrder` выбран на панели рабочей области и отображается в области конструктора.  
  
 ![Представление модели содержимого конструктора схемы XML](../xml-tools/media/xsddesigner-contentmodelview.gif "XSDDesigner_ContentModelView")  
  
## <a name="workspace-panel"></a>Панель рабочей области  
 После добавления узлов в рабочую область, список узлов будет отображаться в **рабочей области** панели представления модели содержимого. При выборе узлов в **рабочей области** панели, они отображаются в области конструктора представления модели содержимого. Чтобы удалить узлы из рабочей, используйте панель инструментов конструктора XSD, **рабочей области** панели контекстного меню или клавишу DELETE.  
  
 Сведения о добавлении узлов см. в разделе «Добавление узлов в рабочую область» в [рабочей области конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md).  
  
## <a name="design-surface"></a>Область конструктора  
 При выборе узла на панели рабочей области, он появляется в области конструктора представления модели содержимого, позволяющей просматривать подробные сведения об узле.  
  
 Модель содержимого узла представлена разворачиваемым графическим деревом с элементами и атрибутами, являющимися узлами дерева. По умолчанию развернут только один уровень. Дополнительные сведения, такие как компоновщики, имена типов, группы и другие контейнеры находятся в вертикальной панели (в развернутом состоянии) вместе с элементами и атрибутами, входящими в них. Если дважды щелкнуть вертикальную панель, она станет горизонтальной, а дерево будет свернуто. Если дважды щелкнуть горизонтальную панель, она станет вертикальной, а дерево будет развернуто. Выбор вертикальной панели выбирает все узлы в контейнере. Если элемент можно разворачивать и сворачивать, то справа от узла появится расширитель.  
  
 Если область конструктора пуста, редактор XML, обозреватель XML-схем и водяной знак не отображаются. *Водяного знака* приведен список ссылок на все представления конструктора XSD. Если набор схем содержит ошибки, в конце списка появится следующий текст: «Воспользуйтесь списком ошибок для просмотра и устранения ошибок в наборе».  
  
## <a name="breadcrumb-bar"></a>Строка навигатора  
 Строка навигатора внизу представления модели содержимого показывает местоположение выбранного узла в наборе схем.  
  
## <a name="context-menus"></a>Контекстные меню  
 Если щелкнуть правой кнопкой мыши элемент в области конструктора или на панели рабочей области, то появится контекстное меню. В следующей таблице приведены параметры, доступные для области конструктора представления модели содержимого.  
  
|Параметр|Описание|  
|------------|-----------------|  
|**Показать в обозревателе XML-схем**|Устанавливает фокус на обозревателе схем и выделяет узел набора схем.|  
|**Показать в представлении графика**|Переключается в представление графика.|  
|**Создание образца XML**|Этот метод предусмотрен только для глобальных элементов. Создает образец XML-файла для глобального элемента.|  
|**Показать документацию**|Показывает или скрывает содержимое узла «Заметка/Документация».|  
|**Экспортируйте схему как рисунок …**|Сохраняет область конструктора в XPS-файле.|  
|**Просмотреть код**|Открывает в редакторе XML-файл, содержащий выбранный узел. Пункт, выбранный в обозревателе XML-схем, будет выбран и в редакторе XML.|  
|**Окно "Свойства"**|Открывает **свойства** окна (если он еще не открыт). В данном окне будут выведены сведения об узле.|  
  
 В следующей таблице приведены параметры поиска, доступные для панели рабочей области.  
  
|Параметр|Описание|  
|------------|-----------------|  
|**Показать в обозревателе XML-схем**|Устанавливает фокус на обозревателе схем и выделяет узел набора схем.|  
|**Показать в представлении графика**|Переключается в представление графика.|  
|**Очистить рабочую область**|Очищает рабочую область и область конструктора.|  
|**Удалить из рабочей области**|Удаляет выбранные узлы из рабочей области и из области конструктора.|  
|**Удалите все, кроме выделенных в рабочей области**|Удаляет узлы, не выделенные в рабочей области и в области конструктора.|  
|**Создание образца XML**|Этот метод предусмотрен только для глобальных элементов. Создает образец XML-файла для глобального элемента.|  
|**Выбрать все**|Выделяет все узлы на панели рабочей области.|  
|**Просмотреть код**|Открывает в редакторе XML-файл, содержащий выбранный узел. Пункт, выбранный в обозревателе XML-схем, будет выбран и в редакторе XML.|  
|**Окно "Свойства"**|Открывает **свойства** окна (если он еще не открыт). В данном окне будут выведены сведения об узле.|  
  
## <a name="properties-window"></a>Окно свойств  
 Используйте контекстное меню, чтобы открыть **свойства** окна. По умолчанию **свойства** окно отображается в правом нижнем углу Visual Studio. Если щелкнуть узел, который отображается в представлении модели содержимого, свойств этого узла будет отображаться в **свойства** окна.  
  
## <a name="xsd-designer-toolbar"></a>Панель инструментов конструктора XSD.  
 Следующие кнопки панели инструментов конструктора XSD включены, если активно представление модели содержимого.  
  
 ![Панель инструментов конструктора схемы XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")  
  
|Параметр|Описание|  
|------------|-----------------|  
|**Показать начальное представление**|Переключается в [начальное представление](../xml-tools/start-view.md). Это представление может осуществляться с помощью сочетания клавиш: **CTRL + 1**.|  
|**Показать представление модели содержимого**|Переключается в [просмотра модели содержимого](../xml-tools/content-model-view.md). Это представление может осуществляться с помощью сочетания клавиш: **CTRL + 2**.|  
|**Показать представление графика**|Переключается в [графическое представление](../xml-tools/graph-view.md). Это представление может осуществляться с помощью сочетания клавиш: **CTRL + 3**.|  
|**Очистить рабочую область**|Очищает рабочую область и область конструктора.|  
|**Удалить из рабочей области**|Удаляет выбранные узлы из рабочей области и из области конструктора.|  
|**Удалите все, кроме выделенных в рабочей области**|Удаляет узлы, не выделенные в рабочей области и в области конструктора.|  
|**Показать документацию**|Показывает или скрывает содержимое узла «Заметка/Документация».|  
  
## <a name="panscroll"></a>Панорамирование/Прокрутка  
 Можно панорамировать область конструктора с использованием полос прокрутки или удерживая нажатой клавишу CTRL при нажатии и перетаскивании мыши. При панорамировании области конструктора с использованием перетаскивания, курсор изменяет свой внешний вид на четыре перекрестные стрелочки, указывающие в четырех направлениях.  
  
## <a name="undoredo"></a>Отменить/Повторить  
 Возможность «отменить/повторить» включена в представлении модели содержимого для следующих действий:  
  
-   Добавление одного узла посредством перетаскивания.  
  
-   Добавление нескольких узлов из окна результатов поиска в обозревателе схемы.  
  
-   Добавление узлов из начального представления.  
  
-   Удаление одного или нескольких узлов.  
  
## <a name="zoom"></a>Масштаб  
 Масштабирование доступно в нижнем правом углу представления модели содержимого.  
  
 Масштабированием можно управлять следующими способами:  
  
-   Удерживая нажатой клавишу CTRL и прокручивая колесико мышки, когда мышь наведена на область представления модели содержимого.  
  
-   Используя ползунковый элемент управления. Ползунок отображает текущий масштаб.  
  
 Ползунок масштаба является непрозрачным, если он выбран, если на него наведена мышка или если вы используете клавишу CTRL с колесиком мышки для увеличения масштаба; во всех остальных случаях он является прозрачным.  
  
## <a name="xml-editor-integration"></a>Интеграция редактора XML  
 Переключаться между конструктором XSD и редактором XML можно, используя контекстное меню.  
  
 Если изменить набор схем в редакторе XML, изменения будут синхронизированы в представлении модели содержимого. Дополнительные сведения см. в разделе [интеграции с помощью редактора XML](../xml-tools/integration-with-xml-editor.md).  
  
## <a name="see-also"></a>См. также  
 [Рабочая область конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md)



