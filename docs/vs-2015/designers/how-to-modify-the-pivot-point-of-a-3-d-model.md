---
title: Практическое руководство. Изменение центра вращения трехмерной модели | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19864f98df2b10d06362969d82752b68b6ba26c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573328"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Практическое руководство. Изменение центра вращения трехмерной модели
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: изменение центра вращения трехмерной модели](https://docs.microsoft.com/visualstudio/designers/how-to-modify-the-pivot-point-of-a-3-d-model).  
  
В этом документе демонстрируется использование редактора моделей для изменения *центра вращения* трехмерной модели. Центр вращения является точкой в пространство, которая определяет математический центр для вращения и масштабирования объекта.  
  
 В этом документе описана следующая операция:  
  
-   Изменение центра вращения объекта  
  
## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Изменение центра вращения трехмерной модели  
 Переопределить центр координат трехмерной модели можно, изменив ее центр вращения.  
  
 Убедитесь, что отображаются окно **Свойства** и **Панель элементов**.  
  
#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>Изменение центра вращения трехмерной модели  
  
1.  Начните с существующей трехмерной модели, как описано в разделе [Практическое руководство. Создание простейшей трехмерной модели](../designers/how-to-create-a-basic-3-d-model.md).  
  
2.  Переключитесь в режим вращения. На панели инструментов **Режим редактора моделей** нажмите кнопку **Режим вращения**, чтобы активировать режим вращения. Вокруг кнопки **Режим вращения** появляется рамка, — это показывает, что редактор моделей теперь находится в режиме вращения. В режиме вращения такие операции, как перенос, влияют на центр вращения объекта, а не на структуру объекта в абсолютном пространстве.  
  
3.  Измените центр вращения объекта. В режиме **Выбрать** выберите объект, а затем на панели инструментов **Средство просмотра моделей**  выберите инструмент **Перенести**. В области конструктора отображается рамка, представляющая центр вращения. Переместите рамку, чтобы изменить центр вращения объекта.  
  
     Перемещая рамку, можно перемещать центр вращения во всех трех измерениях. Чтобы перенести центр вращения по одной оси, переместите стрелку, соответствующую этой оси. Рамка и стрелки приобретают желтый цвет, чтобы указать ось, затронутую переносом.  
  
     Центр вращения также можно указать с помощью свойства **Перенос оси** в окне **Свойства**.  
  
    > [!TIP]
    >  Можно оценить эффект нового центра вращения, повернув объект. Для этого воспользуйтесь инструментом **Поворот** или свойством **Поворот**.  
  
 Ниже показана модель с измененным центром вращения:  
  
 ![Модель дома с измененным центром вращения](../designers/media/digit-modified-model.png "Digit-Modified-Model")  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание простейшей трехмерной модели](../designers/how-to-create-a-basic-3-d-model.md)   
 [Редактор моделей](../designers/model-editor.md)



