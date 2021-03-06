---
title: Поле "Быстрый запуск", папка "Среда", диалоговое окно "Параметры" | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bf2e22db54e064de6716d4ca1325a9e5435318f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558038"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Страница «Быстрый запуск», папка «Среда», диалоговое окно «Параметры»
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [быстрый запуск, среда, диалоговое окно параметров](https://docs.microsoft.com/visualstudio/ide/reference/quick-launch-environment-options-dialog-box).  
  
  
Поле **Быстрый запуск** можно использовать для быстрого поиска и выполнения действий для ресурсов интегрированной среды разработки, таких как параметры, шаблоны и меню. Поле **Быстрый запуск** не подходит для поиска кода и символов. Поле поиска **Быстрый запуск** находится в правом верхнем углу строки меню и доступно при нажатии клавиш CTRL+Q. Просто введите строку поиска в поле. Для поиска строк, содержащих @, используйте «@@».  
  
 **Быстрый запуск** включается по умолчанию при установке Visual Studio. Поле **Быстрый запуск** можно отобразить или скрыть в строке меню, выбрав в меню **Сервис** пункт **Параметры**. Разверните узел **Среды** и выберите **Быстрый запуск**. Установите или снимите флажок **Включить быстрый запуск**. На этой странице можно также включить или отключить категории поиска.  
  
## <a name="category-list"></a>Список категорий  
 Результаты поиска при использовании быстрого запуска отображаются в четырех категориях: **Недавно использовавшиеся**, **Меню**, **Параметры** и **Открытые документы** вместе с количеством элементов в категории. При переходе по результатам поиска по категории нажмите сочетание клавиш Ctrl + Q, чтобы отобразить все результаты из следующей категории. После отображения последней категории сочетание клавиш Ctrl + Q выведет несколько результатов из каждой категории. Сочетание клавиш Ctrl + Shift + Q можно использовать для перемещения по категориям в обратном порядке. Чтобы просмотреть все результаты поиска в категории, выберите имя категории.  
  
 Для ограничения поиска конкретными категориями используются следующие сочетания клавиш.  
  
|Категория|Сочетание клавиш|Описание сочетания клавиш|  
|--------------|--------------|--------------------------|  
|Последние использовавшиеся|@mru<br /><br /> Например `@mru font`.|Отображает не более пяти элементов, которые **использовались последними**.|  
|Меню|@menu<br /><br /> Например `@menu font`.|Ограничивает поиск элементами меню.|  
|Параметры|@opt<br /><br /> Например `@opt font`.|Ограничивает поиск параметрами, заданными в диалоговом окне **Параметры**.|  
|Документы|@doc<br /><br /> Например `@doc font`.|Ограничивает поиск именами файлов и путями к открытым документам, но не выполняет поиск текста внутри самих файлов.|  
  
> [!NOTE]
>  Сочетания клавиш можно изменить на странице **Общие**, **Клавиатура** в диалоговом окне **Параметры**.  
  
## <a name="show-previous-results"></a>Отображение предыдущих результатов  
 По умолчанию вводимое условие поиска не сохраняется между сеансами поиска. Строка поиска очищается, если осуществляется поиск термина, курсор перемещается за пределы области **Быстрый запуск**, а затем возвращается обратно. Чтобы сохранить результаты поиска, перейдите в диалоговое окно **Параметры**, выберите **Быстрый запуск**, а затем установите флажок **Результаты предыдущего поиска при включении быстрого запуска** . При следующем выполнении поиска выйдите из области быстрого запуска, а затем вернитесь обратно. Область быстрого запуска сохранит последнее использовавшееся условие поиска и выведет результаты поиска.  
  
 Самые актуальные советы и рекомендации по использованию поля **Быстрый запуск** см. в [блоге по Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236054).  
  
## <a name="see-also"></a>См. также  
 [Общие элементы пользовательского интерфейса (Visual Studio)](../../ide/reference/general-user-interface-elements-visual-studio.md)   
 [Диалоговое окно "Параметры среды"](../../ide/reference/environment-options-dialog-box.md)



