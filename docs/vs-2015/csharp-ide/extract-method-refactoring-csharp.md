---
title: Извлечение метода рефакторинг (C#) | Документация Майкрософт
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
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7aaa6570382fe296cc58f3d41d451250eafe6537
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572602"
---
# <a name="extract-method-refactoring-c"></a>Рефакторинг для извлечения метода (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Извлечение метода** — это операция рефакторинга, который предоставляет простой способ создать новый метод из фрагмента кода в существующем члене.  
  
 С помощью **извлечение метода**, можно создать новый метод путем извлечения выделенного кода из внутри блока кода существующего члена. Новый, извлеченный метод содержит выделенный код, а выделенный код в существующем члене заменяется вызов нового метода. Превращение фрагмента кода в отдельный метод позволяет быстро и точно реорганизовать код для использования и лучшей читаемости.  
  
 **Извлечение метода** имеет следующие преимущества:  
  
-   Рекомендует рекомендации по написанию, выделяя отдельные, многократно используемые методы.  
  
-   Рекомендует самодокументируемыми кода с помощью хорошей организации.  
  
     Когда описательные имена, используемые методы верхнего уровня можно читать как последовательности комментариев.  
  
-   Способствует созданию детализированных методов для упрощения переопределения.  
  
-   Сокращает дублирование кода.  
  
### <a name="to-use-extract-method"></a>Чтобы использовать извлечение метода  
  
1.  Создайте консольное приложение с именем `ExtractMethod`, а затем замените `Program` на следующий пример кода.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Выберите фрагмент кода, которые нужно извлечь:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  На **рефакторинг** меню, щелкните **извлечение метода**.  
  
     **Извлечение метода** откроется диалоговое окно.  
  
     Кроме того, можно также ввести сочетание клавиш CTRL + R, M, чтобы отобразить **извлечение метода** диалоговое окно.  
  
     Вы можете щелкнуть правой кнопкой выбранного кода, выберите пункт **рефакторинг**, а затем нажмите кнопку **извлечение метода** для отображения **извлечение метода** диалоговое окно.  
  
4.  Укажите имя для нового метода, например `CircleArea`в **новому методу имя** поле.  
  
     Отображает предварительный просмотр новой сигнатуре метода под **Предварительный просмотр сигнатуры метода**.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="remarks"></a>Примечания  
 При использовании **извлечение метода** команды новый метод вставляется после исходного члена в том же классе.  
  
## <a name="partial-types"></a>Разделяемые типы  
 Если класс является разделяемого типа, затем **извлечение метода** создает новый метод сразу же после исходного члена. **Извлечение метода** определяет сигнатуру нового метода, создавая статический метод, когда данные не экземпляр встречается ссылка на код в новый метод.  
  
## <a name="generic-type-parameters"></a>Параметры универсального типа  
 При извлечении метода, имеющего произвольном параметре универсального типа, созданный код не будет добавлять `ref` модификатор в этот параметр только если значение не назначена к нему. Если извлеченный метод будет поддерживать ссылочные типы в качестве аргумента универсального типа, то необходимо вручную добавлять `ref` модификатор параметра в сигнатуре метода.  
  
## <a name="anonymous-methods"></a>Анонимные методы  
 При попытке извлечь часть анонимный метод, который включает ссылку на локальную переменную, которое объявлено или обратиться извне анонимного метода, затем Visual Studio предупредит о возможных изменениях семантики.  
  
 Когда анонимный метод использует значение локальной переменной, значение получается в момент выполнения анонимного метода. При извлечении анонимного метода в другой метод значение локальной переменной получается в момент вызова метода.  
  
 Следующий пример демонстрирует это изменение семантики. Если этот код выполняется, затем **11** выводится на консоль. Если вы используете **извлечение метода** для извлечения области кода, помеченный атрибутом комментарии к коду в отдельный метод и затем выполнить оптимизированный код, затем **10** выводится на консоль.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Чтобы обойти эту проблему, убедитесь, локальные переменные, которые используются в полях анонимного метода класса.  
  
## <a name="see-also"></a>См. также  
 [Рефакторинг (C#)](../csharp-ide/refactoring-csharp.md)