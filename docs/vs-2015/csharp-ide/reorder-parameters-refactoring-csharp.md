---
title: Изменение порядка параметров-рефакторинг (C#) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d0d0428449ce5c78ae098a68d0466262cedd32ef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561051"
---
# <a name="reorder-parameters-refactoring-c"></a>Рефакторинг для упорядочения параметров (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` выполняет Visual C# рефакторинг операцию, которая предоставляет простой способ изменения порядка параметров методов, индексаторов и делегатов. `Reorder Parameters` Изменяет объявление, и во всех местах, где вызывается член, параметров изменяется в соответствии с новым порядком.  
  
 Для выполнения `Reorder Parameters` операции, поместите курсор на или рядом с метода, индексатора или делегата. Если курсор находится в позиции, вызывать `Reorder Parameters` операцию, нажав сочетание клавиш или выбрав соответствующую команду в контекстном меню.  
  
> [!NOTE]
>  Первый параметр метода расширения, не способен упорядочить.  
  
### <a name="to-reorder-parameters"></a>Изменение порядка параметров  
  
1.  Создание библиотеки классов с именем `ReorderParameters`, а затем замените `Class1` на приведенный ниже пример.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Поместите курсор на `MethodB`, в объявлении метода или вызов метода.  
  
3.  На **рефакторинг** меню, щелкните **изменение порядка параметров**.  
  
     **Reorder Parameters** откроется диалоговое окно.  
  
4.  В **Reorder Parameters** выберите `int i` в **параметры** списке и нажмите кнопку «вниз».  
  
     Кроме того, можно перетащить `int i` после `bool b` в **параметры** списка.  
  
5.  В **Reorder Parameters** диалоговом окне щелкните **ОК**.  
  
     Если **Предварительный просмотр изменений ссылок** выбран в **Reorder Parameters** диалоговом окне **Предварительный просмотр изменений — изменение порядка параметров** появится диалоговое окно. Он обеспечивает Предварительный просмотр изменений в списке параметров для `MethodB` в подписи и вызова метода.  
  
    1.  Если **Предварительный просмотр изменений — изменение порядка параметров** появится диалоговое окно, нажмите кнопку **применить**.  
  
         В этом примере объявление метода и метод вызова сайтов для `MethodB` обновляются.  
  
## <a name="remarks"></a>Примечания  
 Можно изменить порядок параметров из объявления метода или вызов метода. Поместите курсор на или рядом с объявление метода или делегата, но не в тексте.  
  
## <a name="see-also"></a>См. также  
 [Рефакторинг (C#)](../csharp-ide/refactoring-csharp.md)