---
title: Задание фонового изображения схемы | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ea74561974db32a831b4123578bffb755a24cbc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561697"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Задание фонового изображения схемы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задание фонового изображения схемы](https://docs.microsoft.com/visualstudio/modeling/setting-a-background-image-on-a-diagram).  
  
С помощью пользовательского кода в пакете SDK для визуализации и моделирования в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно установить фоновое изображение для сгенерированного конструктора.  
  
## <a name="setting-the-background-image"></a>Установка фонового изображения  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Установка фонового изображения для сгенерированного конструктора  
  
1.  Скопируйте файл изображения, который будет использоваться в качестве фона схемы, в каталог Dsl\Resources текущего проекта.  
  
2.  В **обозревателе решений**, щелкните папку Dsl\Resources правой кнопкой мыши, укажите **добавить**, а затем нажмите кнопку **существующий элемент**.  
  
3.  В **добавить существующий элемент** диалоговом окне перейдите в папку Dsl\Resources.  
  
4.  В **файлы типа** выберите **файлы изображений**.  
  
5.  Выберите файл изображения, который был скопирован в каталог и нажмите кнопку **добавить**.  
  
6.  Щелкните правой кнопкой мыши Dsl, а затем нажмите кнопку **свойства** чтобы открыть свойства проекта Dsl.  
  
7.  На **ресурсы** щелкните **этот проект содержит файл ресурсов по умолчанию. Щелкните здесь, чтобы создать ее.**  
  
8.  Добавьте файл изображения в файл ресурсов, перетащив его из **обозревателе решений** в окно ресурсов.  
  
9. Откройте меню "Файл" и выберите параметр для сохранения свойств проекта.  
  
10. Убедитесь, что файл Dsl\Properties\Resources.resx существует и под ним есть файл Resources.Designer.cs.  
  
11. Если файла Resources.Designer.cs нет, выберите файл Resources.resx в **обозревателе решений**.  
  
12. В **свойства** окне `Custom Tool` свойства `ResXFileCodeGenerator`.  
  
13. В **обозревателе решений**щелкните правой кнопкой мыши проект Dsl, выберите **добавить**и нажмите кнопку **новую папку**.  
  
14. Назовите папку **Custom**.  
  
15. Щелкните папку Custom правой кнопкой мыши **добавить**и нажмите кнопку **новый элемент**.  
  
16. В **Добавление нового элемента** отображаемое в диалоговом окне **шаблоны** выберите **файл кода**.  
  
17. В **имя** введите `BackgroundImage.cs`и нажмите кнопку **добавить**.  
  
18. Скопируйте указанный ниже код в файл BackgroundImage.cs, изменив пространство имен, имя класса схемы и имя ресурса файла изображения.  
  
     Замените "MyDiagramClass" на имя частичного класса схемы, определенное в файле Dsl\GeneratedCode\Diagrams.cs. Узнать правильное пространство имен можно также с помощью файла Dsl\GeneratedCode\Diagrams.cs.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Дополнительные сведения о настройке модели с помощью программного кода, см. в разделе [перехода и обновления модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>См. также  
 [Определение фигур и соединителей](../modeling/defining-shapes-and-connectors.md)   
 [Настройка текста полей и изображениями](../modeling/customizing-text-and-image-fields.md)   
 [Переход и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)



