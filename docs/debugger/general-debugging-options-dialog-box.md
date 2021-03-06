---
title: Общие, отладка, диалоговое окно "Параметры" | Документация Майкрософт
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e46301c84b1a9b27eed8cb6667b312ff73af2960
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280641"
---
# <a name="general-debugging-options-dialog-box"></a>Страница "Общие", папка "Отладка", диалоговое окно "Параметры"
**Сервис > Параметры > Отладка > Общие** странице позволяет задать параметры, описанные в этой статье.

Если вам нужно восстановить параметры по умолчанию, можно сделать, используя **средства** > **Импорт и экспорт параметров** > **сбросить все параметры**. Если вы только хотите сбросить подмножество параметров, сохраните параметры в **мастер импорта и экспорта параметров** перед внесением изменений, которые вы хотите протестировать, затем импортировать сохраненные параметры позже.
  
**Запрашивать подтверждение перед удалением всех точек останова** запрашивает подтверждение перед выполнением **удалить все точки останова** команды.  
  
**Прерывать все процессы при прерывании одного** одновременно прерываются все процессы, к которым присоединен отладчик, когда происходит прерывание.  
  
**Прервать в случае исключения пересекают границу AppDomain или управляемым и машинным кодом** управляемого или смешанного режима отладки, среда CLR может перехватывать исключения, которые пересекают границы домена приложения или управляемым и машинным кодом при следующих условия истинны:  
  
1\) когда машинный код вызывает управляемый код с помощью COM-взаимодействия и управляемый код вызывает исключение. См. в разделе [Введение во взаимодействие COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) когда управляемый код, выполняемый в домене приложения 1 вызывает управляемый код домена приложения 2, и код домена приложения 2 создает исключение. См. в разделе [программирование с использованием доменов приложений](/dotnet/articles/framework/app-domains/index).  

3\) когда код вызывает функцию с помощью отражения, и функция создает исключение. См. в разделе [отражения](/dotnet/framework/reflection-and-codedom/reflection).  
  
В списке условие 2 и 3 исключения иногда перехватываются управляемым кодом в `mscorlib` вместо среда CLR. Этот параметр не влияет на прерывание по исключениям, перехватываемым с помощью библиотеки `mscorlib`.  
  
**Включить отладку на уровне адреса** предоставляет дополнительные возможности для отладки на уровне адреса ( **Дизассемблированный код** окне **регистрирует** окна, а точки останова по адресу).  
  
- **Показывать Дизассемблированный код, если источник недоступен** автоматически отображает **Дизассемблированный код** окно при попытке выполнить отладку кода, для которой исходный недоступно.  
  
**Включить фильтры точек останова** позволяет задать фильтры точек останова, чтобы они повлияет только определенные процессы, потоки или компьютеров.  
 
**Используйте новый помощник по исправлению ошибок** позволяет по исправлению (Visual Studio 2017), которая заменяет помощник по исключениям.
  
> [!NOTE]
> Для управляемого кода, этот параметр был ранее вызван **включить помощник по исключениям** . 
  
**Включить только мой код** отладчик отображает и шаг с заходом только код пользователя («Мой код») без учета код системы и другого кода, который является оптимизированным или, не содержащий символов отладки.

- **Выводить предупреждение, если пользовательский код отсутствует при запуске (только управляемый)** при запуске отладки только мой код включен, этот параметр выдает предупреждение, если нет кода пользователя («Мой код»). 

**Включение платформы .NET Framework в исходном коде** позволяет отладчику шаг с заходом в исходный код .NET Framework. Включение этого параметра автоматически отключает режим "Только мой код". В расположение кэша будут загружены символы .NET Framework. Можно изменить расположение кэша в **параметры** диалоговом окне **Отладка** категории **символы** страницы.  
  
**Обход свойств и операторов (только управляемый код)** запрещает отладчику шаг с заходом в свойства и операторы в управляемом коде.  
  
**Включить вычисление свойств и другие неявные вызовы функций** вызывает Включение автоматического вычисления свойств и неявный вызов функции в окнах переменных и **"Быстрая проверка"** диалоговое окно.  
  
- **Вызов функции преобразования строк для объектов в окнах переменных (C# и JavaScript только)** выполняет вызов функции преобразования неявных строковых при вычислении объектов в окнах переменных. Результат отображается в виде строки вместо имени типа. Применимо только при отладке кода C#. Этот параметр можно переопределить с помощью атрибута DebuggerDisplay (см. в разделе [использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Включение поддержки исходного сервера** указывает отладчику Visual Studio для получения исходных файлов с исходных серверов, которые реализуют SrcSrv (`srcsrv.dll`) протокола. Team Foundation Server и инструменты отладки для Windows — два исходных сервера, которые реализуют этот протокол. Дополнительные сведения о настройке SrcSrv см. в разделе [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) документации. Кроме того, см. в разделе [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Так как чтение *.pdb* файлов можно выполнить произвольный код в файлах, убедитесь, что вы доверяете серверу.  
  
- **Выводить диагностические сообщения сервера системы управления версиями в окно вывода** при включенной поддержке сервера источника, этот параметр включает вывод диагностических сведений.  
  
- **Разрешить исходного сервера для частично доверенных сборок (только управляемый код)** при включенной поддержке сервера источника, этот параметр переопределяет поведение по умолчанию для неизвлечения исходного частично доверенных сборок.  

**Включить поддержку ссылок на источник** указывает отладчику Visual Studio загружает исходные файлы для PDB-файлы, содержащие ссылки на исходные сведения. Дополнительные сведения о ссылки на источник, см. в разделе [спецификация источника ссылки](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Выделять всю исходную строку для точек останова и текущего оператора (только C++)** при отладчик выделяет точки останова и текущего оператора, он выделяет всю строку.  
  
**Требовать точного соответствия исходной версии файлов** работу отладчика, чтобы убедиться, что исходный файл совпадает с версией исходного кода, используемого для создания исполняемого файла отладки. Если версии не совпадают, вам будет предложено найти соответствующий источник. Если соответствующий исходный код не найден, в процессе отладки исходный код не отображается. 
  
**Перенаправлять весь текст окна выходных данных в окно интерпретации** перенаправление всех сообщений, которые обычно отображаются в отладчика **вывода** окно, чтобы **Интерпретация** окно вместо этого.  
  
**Показывать базовую структуру объектов в окнах переменных** приводит к отключению всех пользовательских настроек представления структуры объектов. Дополнительные сведения о настройках представлений см. в разделе [Создание настраиваемых представлений собственных объектов](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Отключать JIT-оптимизацию при загрузке модуля (только управляемый код)** отключает JIT-оптимизации управляемого кода при загрузке модуля и JIT-компиляции, пока отладчик присоединен. Отключение оптимизации позволяет упростить процесс отладки некоторых проблем, однако может отрицательно сказаться на производительности. В режиме "Только мой код" при отключении JIT-оптимизации в коде пользователя ("Мой код") может отображаться посторонний код. Дополнительные сведения см. в разделе [JIT-оптимизацию и отладка](../debugger/jit-optimization-and-debugging.md).

**Включить отладку JavaScript для ASP.NET (Chrome и Internet Explorer)** позволяет отладчику скриптов для приложений ASP.NET. При первом использовании в браузере Chrome необходимо войти в браузер при первом использовании, чтобы включить расширения Chrome, установленные ранее. Отключите этот параметр, чтобы вернуться к поведению предыдущих версий.    

**Загружать экспортированные dll** загружает таблицы экспорта библиотеки dll. Символьные данные из таблиц экспорта библиотеки DLL можно использовать при работе с сообщениями Windows, процедурами Windows (WindowProcs), COM-объектами, при маршалинге или при работе с любой библиотекой DLL, для которой нет символов. Считывание данных экспорта библиотеки DLL связано с определенными дополнительными затратами. Поэтому данная возможность по умолчанию отключена.  
  
Чтобы увидеть, какие символы доступны в таблице экспорта библиотеки DLL, используйте `dumpbin /exports`. Символы доступны для любой 32-разрядной системной библиотеки DLL. В выходных данных команды `dumpbin /exports` можно увидеть точное имя функции, включая символы, отличные от буквенно-цифровых. Это полезно при задании точки останова в функции. Имена функций из таблиц экспорта библиотеки DLL могут отображаться в отладчике в сокращенном виде. Вызовы функций перечисляются в том порядке, в котором эти функции вызываются, при этом текущая функция (наиболее глубоко вложенная) располагается наверху. Дополнительные сведения см. в разделе [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Показать параллельную диаграмму с накоплением нижней вниз** определяет направление, в котором отображаются стеки в **Параллельные стеки** окна.
  
**Игнорировать исключения обращения к памяти GPU, если записываемые данные не изменили значение** пропускает состояния гонки, обнаруженные во время отладки, если данные не изменили. Дополнительные сведения см. в разделе [отладка кода GPU](../debugger/debugging-gpu-code.md).  
  
**Использовать режим совместимости управляемого кода** заменяет значение по умолчанию ядро отладки по на предыдущую версию для поддержки следующих сценариев:  
  
- Вы используете отличный от C#, VB и F# язык платформы .NET Framework, который предоставляет собственный вычислитель выражений (в том числе C++/CLI).  
  
- Необходимо включить операцию "Изменить и продолжить" для проектов C++ в смешанном режиме отладки.  
  
> [!NOTE]
> Выбор совместимости управляемого режима отключению некоторых функций, реализованных только в ядре отладки по умолчанию. 

**Использовать устаревшие вычислители выражений C# и VB** отладчик будет использовать вычислители выражений Visual Studio 2013 C# и Visual Basic, а не вычислители выражений на основе Visual Studio 2015 Roslyn.    
  
**Предупреждать об использовании настраиваемых визуализаторов отладчика для потенциально небезопасных процессов (только управляемый код)** Visual Studio предупреждает при использовании настраиваемого визуализатора отладчика, на котором выполняется код в отлаживаемом объекте, так как он может быть запущен в unsafe код.  
  
**Включить распределитель кучи отладки Windows (только машинный код)** позволяет отладочной куче windows улучшать диагностику кучи. Включение этого параметра повлияет на производительность отладки.  
  
**Включить инструменты отладки пользовательского интерфейса для XAML** динамического визуального дерева и динамического обозревателя свойств windows будет отображаться при запуске отладки (F5) поддерживаемого типа проекта. Дополнительные сведения см. в разделе [свойства проверять XAML во время отладки](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Предварительный просмотр выбранных элементов в динамическом визуальном дереве** элемент XAML, контекст которого выбран выбирается в **динамическое визуальное дерево** окна.  
  
- **Показать средства среды выполнения в приложении** показывает **динамическое визуальное дерево** команды в панели инструментов в главном окне отлаживаемого приложения XAML. Этот параметр впервые появился в Visual Studio 2015 с обновлением 2. 

- **Включить XAML, изменить и продолжить** позволяет использовать изменить и продолжить для кода XAML. 
  
**Включить средства диагностики при отладке** **средства диагностики** окно отображается при отладке.
  
**Показывать подсказку с затраченным временем при отладке** окно кода отображает время вызова этого метода при отладке.  
  
**Включить изменить и продолжить** можно использовать изменить и продолжить функциональные возможности во время отладки.  
  
- **Включить собственный изменить и продолжить** можно использовать изменить и продолжить функциональные возможности при отладке машинного кода C++. Дополнительные сведения см. в разделе [изменить и продолжить (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Применить изменения при продолжении (только машинный код)** Visual Studio автоматически компилирует и применяет необработанные изменения кода внесенные при продолжении процесса из состояния приостановки. Если не выбран, можно применить изменения с помощью элемента «Применить изменения кода» в меню "Отладка".  
  
- **Предупреждать об устаревшем коде (только машинный код)** получать предупреждения об устаревшем коде.    

**Показать выполнения нажмите кнопку в редакторе во время отладки** при выборе этого параметра, [выполнение до щелкнутого](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) кнопка будет присутствовать во время отладки.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Параметры, поддерживаемые в предыдущих версиях Visual Studio

Если вы используете более старой версии Visual Studio, может присутствовать некоторые дополнительные параметры.

**Включить помощник по исключениям** для управляемого кода включен помощник по исключениям. В Visual Studio 2017 по исправлению заменен по исключениям.

**Очищать стек вызовов от кадров необработанных исключений** вызывает **стек вызовов** окно, чтобы вернуться стек вызовов в точке, перед возникновением необработанного исключения. 

**Предупреждать об отсутствии символов при запуске (только машинный код)** отображает диалоговое окно предупреждения при попытке отладки программы, для которого нет информация о символах отладчик. 

**Предупреждать, если отладка скриптов запрещена при запуске** при запуске отладчика с отключенной отладкой скриптов отображается диалоговое окно предупреждения.

**Использование собственного режима совместимости** при выборе этого параметра отладчик использует собственный отладчик Visual Studio 2010 вместо нового отладчика машинного кода.  
  
Этот параметр следует использовать при отладке кода .NET C++, так как новое ядро отладки не поддерживает вычисление выражений .NET C++. Однако включение режима совместимости машинного кода отключает множество возможностей, которые зависят от работы текущей реализации отладчика. Например, модуль предыдущих версий отсутствуют многие визуализаторы для встроенных типов, таких как `std::string` в проектах Visual Studio 2015.   Используйте проекты Visual Studio 2013 для оптимальной производительности отладки в таких случаях.
  
## <a name="see-also"></a>См. также  
 [Отладка в Visual Studio](../debugger/index.md)  
 [Обзор функций отладчика](../debugger/debugger-feature-tour.md)
