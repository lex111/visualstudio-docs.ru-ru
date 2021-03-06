---
title: JavaScript в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677a022d314204cf5a49c64380aa5301aa170a47
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561901"
---
# <a name="javascript-in-visual-studio"></a>JavaScript в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [JavaScript в Visual Studio](https://docs.microsoft.com/visualstudio/javascript/javascript-in-visual-studio).  
  
JavaScript — полноправный язык в Visual Studio. При написании кода JavaScript в интегрированной среде разработки Visual Studio можно использовать большинство или все стандартные средства редактирования (фрагменты кода, IntelliSense и т. д.). Код JavaScript можно написать для многих типов приложений и служб.  
  
 См. справочную документацию по языку [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Определенные версии Visual Studio или специальные расширения Visual Studio могут потребоваться для разработки конкретных типов приложений и служб с помощью HTML и JavaScript. В следующем списке приводятся ссылки на дополнительные сведения.  
  
-   Для создания кроссплатформенных приложений с помощью Apache Cordova [доступны средства Visual Studio для Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Для создания приложений для платформ [Магазин Windows](http://dev.windows.com/develop) и [Windows Phone](http://dev.windows.com/develop) (а также универсальных приложений с поддержкой двух этих платформ) [доступны эти средства](http://dev.windows.com/en-us/develop/downloads).  
  
-   Для создания облачных служб посетите [сайт Microsoft Azure](http://azure.microsoft.com/documentation/).  
  
-   Для создания веб-сайтов и веб-приложений посетите [сайт ASP.NET](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Можно создать пустой веб-сайт ASP.NET и использовать его для программирования кода HTML, CSS и JavaScript. Файл Webconfig, предоставляемый ASP.NET, дает возможность выполнять отладку в Visual Studio (кроме того, при запуске приложения можно использовать инструменты F12).  
  
 Редактор JavaScript в Visual Studio обеспечивает поддержку IntelliSense. См. дополнительные сведения об [IntelliSense для JavaScript](../ide/javascript-intellisense.md).  
  
## <a name="whats-new-in-javascript"></a>Новые возможности JavaScript  
 Новые функции для JavaScript перечислены в следующей таблице.  
  
|Функция|Описание|  
|-------------|-----------------|  
|Классы|Новый синтаксис поддерживает объявление [классов](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/class-statement-javascript.md).|  
|Обещания|[Обещания](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/promise-object-javascript.md) упрощают создание асинхронного и более чистого кода. Конструкторы обещаний поддерживаются вместе со служебными методами `all` и `race`.|  
|Итераторы|Теперь можно выполнить итерацию поддерживающих итерацию объектов (включая массивы, объекты, похожие на массивы, и итераторы), вызывая пользовательский обработчик итераций с операторами, которые должны быть исполнены для значения каждого свойства по отдельности. См. дополнительные сведения см. об [итераторах и генераторах](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/advanced/iterators-and-generators-javascript.md). **Примечание.** Генераторы пока не поддерживаются.|  
|Функции со стрелкой|Функция со стрелкой (=>) предоставляет сокращенный синтаксис для ключевого слова `function` с лексической привязкой `this`.|  
|Новые методы для встроенных объектов|Встроенные объекты [Array Object](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/array-object-javascript.md), [Math Object](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/math-object-javascript.md), [Number Object](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/number-object-javascript.md), [Object Object](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/object-object-javascript.md) и [String Object](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/string-object-javascript.md) предоставляют множество новых служебных функций и свойств для обработки и инспектирования данных.|  
|Усовершенствования объектного литерала|Объекты теперь поддерживают вычисляемые свойства, точные определения методов и сокращенный синтаксис для свойств, значения которых инициализируются в переменную с таким же именем. См. дополнительные сведения о [создании объектов](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/creating-objects-javascript.md).|  
|Прокси-элементы|[Прокси-элементы](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/proxy-object-javascript.md) позволяют настраивать пользовательское поведение объектов.|  
|Параметры Rest|Параметры Rest позволяют преобразовать последовательные аргументы в вызове функции в массив. См. дополнительные сведения о [функциях](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/functions-javascript.md).|  
|Оператор Spread|[Оператор spread](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`…`) расширяет доступные для итерации выражения в отдельные аргументы. Например, `a.b(…array)` примерно равен `a.b.apply(a, array)`.|  
|Символы|Объекты [Symbol](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/symbol-object-javascript.md) позволяют добавлять свойства в существующие объекты без создания помех существующим свойствам объектов, непредусмотренной видимости и других несогласованных дополнений, которые могут быть реализованы другими частями кода.|  
|Строки шаблона|[Строки шаблона](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/advanced/template-strings-javascript.md) — это строковые литералы, позволяющие оценивать выражения и сцеплять их со строковым литералом.|  
|Усовершенствования Юникода|Была усовершенствована поддержка Юникода. Так, новый формат escape-последовательности поддерживает астральные кодовые точки (кодовые точки с более 4 шестнадцатеричных цифр). См. дополнительные сведения о [специальных символах](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/advanced/special-characters-javascript.md).|  
|Множество WeakSet|Множество [WeakSet](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/weakset-object-javascript.md) — это коллекция объектов, которая будет удалена как мусор при отсутствии доступных ссылок на нее.|

