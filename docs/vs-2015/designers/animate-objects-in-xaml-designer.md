---
title: Анимирование объектов в конструкторе XAML | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 481ba0f156f6ea6cc43d9df19eedcb84ab864cbe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559233"
---
# <a name="animate-objects-in-xaml-designer"></a>Анимирование объектов в конструкторе XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [анимирование объектов в конструкторе XAML](https://docs.microsoft.com/visualstudio/designers/animate-objects-in-xaml-designer).  
  
Вы можете создавать короткие анимации, которые перемещают объекты или позволяют им исчезать и появляться.  
  
 Чтобы начать работу, создайте *раскадровку*. Раскадровка содержит одну или несколько *временных шкал*. Задайте *опорные кадры* на временной шкале, чтобы отметить изменения свойств. Затем при запуске анимации Blend интерполирует изменения свойств за указанный период времени. Результатом является плавный переход. Вы можете анимировать любое свойство, которое принадлежит к объекту, даже если оно не является визуальным.  
  
 На следующем рисунке показана раскадровка под названием **MoveUp**. Временная шкала содержит ключевые кадры, которые отмечают позиции X и Y прямоугольника. При запуске анимации прямоугольник плавно перемещается из одной позиции в другую.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Посмотрите следующие видео, чтобы узнать, как создавать анимацию.  
  
|Ознакомьтесь с коротким видео.|Получите следующие сведения:|  
|--------------------------|-------------------|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Создание временных шкал](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Создание временной шкалы и работа с объектами временной шкалы.|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Добавление опорных кадров и повторение анимации](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Добавьте ключевые кадры и задайте свойства для каждого ключевого кадра. Затем запустите анимацию, и вы увидите, как объекты плавно перемещаются между ключевыми кадрами.|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Добавление триггеров событий для обеспечения интерактивности](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Запуск анимации при возникновении события. Например, анимация запустится при загрузке окна.|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Анимация цветов](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Используйте анимацию для изменения цвета объекта.|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Создание и изменение путей перемещения](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Анимация объектов для всего пути.|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Плавность опорных кадров](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Ускорение или замедление анимации в начале (*замедление в начале*) или к концу (*замедление в конце*) анимации.|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Анимация кнопки](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Создание интересных эффектов, которые отображаются на кнопке при наведении на нее курсора.|  
|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Создание анимации и работа с плавностью](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Анимация эффектов, которые отображаются в том случае, когда пользователь нажимает кнопку на изображении калькулятора.|  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского интерфейса с помощью Blend для Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)



