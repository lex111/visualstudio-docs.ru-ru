---
title: Узнайте, как Отладка многопоточных приложений
description: Отладка с помощью окна "Параллельные стеки" и "контроль параллельных данных" в Visual Studio
ms.custom: H1HackMay2017
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11cb05ea81f086cf8c26e3058850968a909b84e3
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468687"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Начало отладки многопоточных приложений в Visual Studio
Visual Studio предоставляет несколько средств и элементы пользовательского интерфейса для отладки многопоточных приложений. Этом руководстве показано, как использовать маркеры потоков **Параллельные стеки** окне **контроль параллельных данных** окна, условные точки останова и фильтр точки останова. В этом руководстве всего несколько минут, но оно позволит ознакомиться вас с функциями для отладки многопоточных приложений.

|         |         |
|---------|---------|
|  ![значок кинокамеры для видео](../install/media/video-icon.png "Просмотреть видео")  |    [Ознакомьтесь с видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) на многопотоковая отладка, показывающая те же действия. |

Другие разделы дополнительных сведений об использовании других многопоточных средств отладки:

- Для подобных раздел, в котором показано, как использовать **место отладки** инструментов и **потоков** окно, см. в разделе [Пошаговое руководство: отладка многопоточного приложения](../debugger/how-to-use-the-threads-window.md).

- Для подобных раздела с пример, использующий <xref:System.Threading.Tasks.Task> (управляемый код) и среда выполнения с параллелизмом (C++), см. в разделе [Пошаговое руководство: отладка параллельного приложения](../debugger/walkthrough-debugging-a-parallel-application.md). Общие отладки советы, которые применяются к типам наиболее многопоточного приложения см. в этом разделе и соответствующей статье.
  
Для работы с этим руководством, необходим проект многопоточного приложения. Выполните следующие действия для создания этого проекта.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Чтобы создать проект многопоточного приложения  
  
1.  На **файл** меню, выберите **New** и нажмите кнопку **проекта**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2.  Выберите язык по своему усмотрению: **Visual C#**, **Visual C++**, или **Visual Basic**.  
  
3.  В разделе **Windows Desktop**, выберите **консольное приложение**.  
  
4.  В **имя** введите имя MyThreadWalkthroughApp поле.  
  
5.  Нажмите кнопку **ОК**.  
  
     Появится новый проект консольного приложения. Когда проект будет создан, откроется файл исходного кода. В зависимости от языка, которую вы выбрали исходный файл может называться Module1.vb, Program.cs и MyThreadWalkthroughApp.cpp.  
  
6.  Удалите код, который отображается в исходном файле и замените в примере кода показано ниже.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  На **файл** меню, щелкните **сохранить все**.  
  
#### <a name="to-begin-the-tutorial"></a>Для работы с этим руководством  
  
-   В редакторе исходного кода найдите следующий код: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Начало отладки  
  
1.  Щелкните в левом поле `Thread.Sleep` или `this_thread::sleep_for` инструкцию, чтобы добавить новую точку останова.  
  
     Во внутренней области в левой части редактора исходного кода появится красный кружок. Это означает, что точка останова установлена в этом месте. 
  
2.  На **Отладка** меню, щелкните **начать отладку** (**F5**).  
  
     Visual Studio создает решение, приложение начинает выполняться с подключенным отладчиком, и затем приложение останавливается в точке останова.  
  
    > [!NOTE]
    > При переключении фокуса в окно консоли, нажмите кнопку в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] окно для возвращения фокуса в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  В редакторе исходного кода найдите строку, содержащую точку останова:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Чтобы обнаружить маркер потока  

1.  На панели инструментов отладки, нажмите кнопку **Показать потоки в исходном коде** кнопку ![Показать потоки в исходном коде](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Нажмите клавишу **F11** один раз, чтобы перейти к строке кода отладчиком по одному.
  
3.  Посмотрите на переплет в левой части окна. В этой строке, вы увидите *маркер потока* значок ![маркер потока](../debugger/media/dbg-thread-marker.png "ThreadMarker") , похож на 2 тряпичных нити. маркер потока указывает, что некий поток остановлен в этом месте.

    Обратите внимание на то, что маркер потока может быть частично скрыт с помощью точки останова. 
  
4.  Наведите указатель мыши на маркер потока. Появится подсказка. Подсказка сообщает имя и идентификационный номер каждого остановившегося тут потока. В этом случае имя является, вероятно, `<noname>`. 
  
5.  Щелкните правой кнопкой мыши маркер потока, чтобы просмотреть доступные параметры в контекстном меню.
    
## <a name="ParallelStacks"></a>Просмотр расположения потоков

В **Параллельные стеки** окно, можно переключаться между представление "Потоки" и (для программирования на основе задач) представление "задачи" и вы можете просмотреть стек вызовов для каждого потока. В этом приложении можно использовать представление "Потоки".

1. Откройте **Параллельные стеки** окно, выбрав **Отладка > Windows > параллельных стеков**. Вы увидите примерно следующим образом (точные сведения будут отличаться в зависимости от текущего расположения, каждый поток, оборудования и языка программирования).

    ![Параллельных стеков окно](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    В этом примере слева направо мы получаем эти сведения для управляемого кода:
    
    - Основной поток (слева) остановлена на `Thread.Start` (точка останова обозначается значком маркер потока ![маркер потока](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Два потока ввода `ServerClass.InstanceMethod`, один из которых является текущий поток (желтая стрелка), пока другой поток остановлен в `Thread.Sleep`.
    - Также запускает новый поток (справа) (остановлено на `ThreadHelper.ThreadStart`).

2.  Щелкните правой кнопкой мыши записи в **Параллельные стеки** окно, чтобы просмотреть доступные параметры в контекстном меню.

    Можно выполнять различные действия из этих меню щелкните правой кнопкой мыши, но в этом руководстве мы покажем несколько из этих сведений в **контроль параллельных данных** окна (в следующих разделах).

    > [!NOTE]
    > Если пользователи будут заинтересованы в просмотре списка просмотра со сведениями о каждом потоке, используйте **потоков** окно вместо этого. См. в разделе [Пошаговое руководство: отладка многопоточного приложения](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Установка контрольных значений для переменной

1. Откройте **контроль параллельных данных** окно, выбрав **Отладка > Windows > контроль параллельных данных > контроль параллельных данных 1**.

2. Щелкните ячейку, где встречается `<Add Watch>` текста (или пустой заголовок ячейки в четвертом столбце), тип `data`, и нажмите клавишу ВВОД.

    В окне отображаются значения для переменной данных для каждого потока.

3. Снова щелкните ячейку, где встречается `<Add Watch>` текста (или пустой заголовок ячейки в столбце 5-й), тип `count`, и нажмите клавишу ВВОД.

    В окне отображаются значения для переменной счетчика для каждого потока. (Если вы не видите еще такой большой объем сведений, попробуйте еще несколько раз нажимать клавишу F11, чтобы переместить выполнение потоков в отладчике.)

    ![Параллельное окно контрольных значений](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Щелкните правой кнопкой мыши одну из строк в окне, чтобы увидеть доступные параметры.

## <a name="flagging-and-unflagging-threads"></a>Пометка потоков и ее снятие  
Можно пометить поток, которые требуется уделить особое внимание. Пометка потоков — хороший способ, чтобы отслеживать важные потоки и игнорировать потоков, которые вас не интересует.  
  
#### <a name="to-flag-threads"></a>Чтобы пометить потоки  

1. В **контроль параллельных данных** окна, удерживая нажатой клавишу SHIFT и выбрать несколько строк.

2. Щелкните правой кнопкой мыши и выберите **флаг**.

    Теперь помечаются все выбранные потоки. Теперь можно фильтровать на показ только помеченных потоков.
  
3.  В **контроль параллельных данных** окна, найдите **Показывать только отмеченные потоки** кнопку ![Показывать отмеченные потоки](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Нажмите кнопку **Показывать только отмеченные потоки** кнопки.  
  
    Теперь в списке отображаются только отмеченные потоки.

    > [!TIP]
    > Когда Вы отметили некоторые потоки, можно правой кнопкой мыши строку кода в редакторе кода и выбрать **Запустить помеченные потоки до курсора** (Убедитесь, что выбрать достигнет кода, что все отмеченные потоки). Это будет приостанавливать потоки в выбранной строке кода, что упрощает для управления порядком выполнения по [Замораживание и размораживание потоков](#bkmk_freeze).

5.  Нажмите кнопку **Показывать только отмеченные потоки** кнопку для переключения обратно в **Показывать все потоки** режим.
    
#### <a name="to-unflag-threads"></a>Чтобы снять отметку с потока

Снять отметку с потока, щелкнуть правой кнопкой мыши один или несколько отмеченных потоков в **контроль параллельных данных** окна и выберите **снять отметку**.

## <a name="bkmk_freeze"></a> Замораживание и размораживание потоков 

> [!TIP]
> Можно заморозить или разморозить (приостанавливать и возобновлять) потоки можно управлять порядком, в котором потоки выполнения работы. Это может помочь устранить проблемы параллелизма, например взаимоблокировки и состояния гонки.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Чтобы заморозить и разморозить потоки  
  
1.  В **контроль параллельных данных** окно с всех выбранных строк, щелкните правой кнопкой мыши и выберите **закрепить**.

    Значок паузы во втором столбце, теперь отображается для каждой строки. Значок паузы указывает, что поток заморожен.

2.  Отмените выбор строк, нажав кнопку только одну строку.

3.  Щелкните правой кнопкой мыши строку и выберите **Разморозить**.

    Значок паузы исчезает на этой строке, указывающее, что поток не приостановлен.

4.  Перейдите в редактор кода и **F11**. Только незафиксированных поток выполняется.

    Приложение также может создавать экземпляры некоторых новых потоков. Обратите внимание, что все новые потоки без отметки и заморожены.

## <a name="bkmk_follow_a_thread"></a> Выполните один поток с помощью условных точек останова

В некоторых случаях может быть полезным следить за выполнением из одного потока в отладчике. Это можно сделать одним из способов является замораживание потоков, которые вас не интересуют, но в некоторых случаях вы можете следовать один поток не замораживание других потоков (для конкретной ошибки, например данные для воспроизведения). Чтобы выполнить поток без замораживание других потоков, необходимо избегать Приостановка выполнения кода, за исключением случаев, в том потоке, которые вас интересуют. Это можно сделать, задав [условную точку останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Можно установить точки останова на различных условиях, например имя или идентификатор потока. Другой метод, который может оказаться полезным является задайте условие для данных, вы знаете, будет уникальным для каждого потока. Это распространенный сценарий отладки, который вас интересует более в некоторые данные определенного типа чем любого конкретного потока.

#### <a name="to-follow-a-single-thread"></a>Для выполнения одного потока

1. Щелкните правой кнопкой мыши созданную ранее точку останова и выберите **условия**.

2. В **параметры точки останова** введите `data == 5` для условного выражения.

    ![Условную точку останова](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Если вас интересуют более конкретного потока, затем используйте имя или идентификатор потока для условия. Для этого в **параметры точки останова** выберите **фильтра** вместо **условное выражение**и следуйте советам фильтра. Можно присвоить имя потоков в коде приложения (поскольку потоки идентификаторы изменить при повторном запуске отладчика).

3. Закрыть **параметры точки останова** окна.

4. Нажмите кнопку перезапуска ![перезапустить приложение](../debugger/media/dbg-tour-restart.png "RestartApp") кнопку, чтобы перезапустить сеанс отладки.

    Произойдет останов в коде в потоке, для которого переменную данных — 5. Найдите желтая стрелка (текущий контекст отладчика) в **контроль параллельных данных** окно, чтобы убедиться, что.

5. Теперь можно шаг с обходом кода (F10) и шаг с заходом (F11) кода и следить за выполнением один поток.

    Пока условие точки останова является уникальным для потока, и отладчик не достигнет других точек останова в других потоках (может потребоваться отключить их), вы выполните шаг с обходом кода и пошаговое выполнение кода без переключения для других потоков.

    > [!NOTE]
    > При переходе отладчика будет выполняться все потоки. Тем не менее отладчик не будет останавливаться в код в других потоках, если один из других потоков достигает точки останова. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Дополнительные сведения о многопоточных диалоговых окон отладки 

#### <a name="to-switch-to-another-thread"></a>Для переключения на другой поток 

- Чтобы переключиться на другой поток, см. в разделе [как: переключиться в другой поток во время отладки](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Дополнительные сведения о окна параллельных стека и контроль параллельных данных  
  
- См. в разделе [как: использование окна параллельных стека](../debugger/using-the-parallel-stacks-window.md) 

- См. в разделе [как: использование окна параллельных контрольных значений](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Практическое руководство. Переключение на другой поток при отладке](../debugger/how-to-switch-to-another-thread-while-debugging.md)
