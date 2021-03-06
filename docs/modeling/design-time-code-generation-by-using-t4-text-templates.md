---
title: Создание кода во время разработки с помощью текстовых шаблонов T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: abb606712365108c869ee0cfe705359ad6064228
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860411"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Создание кода во время разработки с помощью текстовых шаблонов T4
Текстовые шаблоны времени разработки T4 позволяют создавать программный код и другие файлы в проект Visual Studio. Как правило, шаблоны создаются таким образом, чтобы они различаются в код, который они создают в соответствии с данными из *модели*. Модель — это файл или базу данных, которая содержит основные сведения о требованиях приложения.

 Например, можно создать модель, которая определяет рабочий процесс как таблицу или схему. На основе модели можно создать программу, выполняющую рабочий процесс. При изменении потребностей пользователей, это просто обсудить новый рабочий процесс с пользователями. Повторное создание кода на основе рабочего процесса надежнее, чем обновление кода вручную.

> [!NOTE]
>  Объект *модели* — это источник данных, который описывает определенный аспект приложения. Она может быть представлена в любой форме, в виде файла или базы данных. Она не должна соответствовать определенной форме, например как модель UML или модель для доменного языка (DSL). Типичные модели создаются в форме таблиц или XML-файлов.

 Вероятно, вы уже знакомы с созданием кода. При определении ресурсов в **.resx** автоматически создается файл в решение Visual Studio, набор классов и методов. Файл ресурсов обеспечивает более простое и надежное редактирование ресурсов по сравнению с внесением изменений в классы и методы. Используя текстовые шаблоны, можно создавать код таким же образом на основе вашего собственного источника.

 Текстовый шаблон содержит сочетание текста, который требуется создать, и программного кода, создающего переменные части текста. Программный код позволяет повторять или, при определенных условиях, пропускать части созданного текста. Созданный текст сам по себе может быть программным кодом, который формирует часть вашего приложения.

## <a name="creating-a-design-time-t4-text-template"></a>Создание текстового шаблона времени разработки T4

#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>Создание шаблона времени разработки T4 в Visual Studio

1.  Создание проекта Visual Studio или откройте существующий.

     Например, на **файл** меню, выберите **New** > **проекта**.

2.  Добавьте файл текстового шаблона в проект и присвойте ему имя с расширением **.tt**.

     Для этого в **обозревателе решений**, в контекстном меню проекта выберите **добавить** > **новый элемент**. В **Добавление нового элемента** диалогового окна выберите **текстового шаблона** в средней области.

     Обратите внимание, что **пользовательское средство** свойство файла **TextTemplatingFileGenerator**.

3.  Откройте файл. Он будет содержать следующие директивы:

    ```
    <#@ template hostspecific="false" language="C#" #>
    <#@ output extension=".txt" #>
    ```

     Если вы добавили шаблон в проект [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], для атрибута языка будет задано значение `VB`.

4.  Добавьте любой текст в конец файла. Например:

    ```
    Hello, world!
    ```

5.  Сохраните файл.

     Может появиться **предупреждение системы безопасности** окно с запросом подтверждения запуска шаблона. Нажмите кнопку **ОК**.

6.  В **обозревателе решений**, разверните узел файла шаблона, и вы увидите файл с расширением **.txt**. Файл содержит текст, созданный на основе шаблона.

    > [!NOTE]
    >  Если проект является проектом Visual Basic, необходимо нажать кнопку **Показать все файлы** чтобы увидеть выходной файл.

### <a name="regenerating-the-code"></a>Повторное создание кода
 Шаблон выполняется, создавая дочерний файл, в следующих случаях:

-   Изменение шаблона и перемещении фокуса в другое окно Visual Studio.

-   при сохранении шаблона;

-   Нажмите кнопку **преобразовать все шаблоны** в **построения** меню. Это приведет к преобразованию всех шаблонов в решении Visual Studio.

-   В **обозревателе решений**, в контекстном меню любого файла, выберите **пользовательское средство**. Используйте этот метод для преобразования выбранного набора шаблонов.

 Можно также настроить проект Visual Studio, чтобы шаблоны выполнялись при изменении считываемых ими файлов данных. Дополнительные сведения см. в разделе [автоматическое повторное создание кода](#Regenerating).

## <a name="generating-variable-text"></a>Создание переменного текста
 Текстовые шаблоны позволяют программному коду изменять содержимое созданного файла.

#### <a name="to-generate-text-by-using-program-code"></a>Создание текста с помощью программного кода

1.  Измените содержимое файла `.tt`:

    ```csharp
    <#@ template hostspecific="false" language="C#" #>
    <#@ output extension=".txt" #>
    <#int top = 10;

    for (int i = 0; i<=top; i++)
    { #>
       The square of <#= i #> is <#= i*i #>
    <# } #>
    ```

    ```vb
    <#@ template hostspecific="false" language="VB" #>
    <#@ output extension=".txt" #>
    <#Dim top As Integer = 10

    For i As Integer = 0 To top
    #>
        The square of <#= i #> is <#= i*i #>
    <#
    Next
    #>

    ```

2.  Сохраните TT-файл и снова проверьте созданный TXT-файл. В нем перечисляются квадратные корни чисел от 0 до 10.

 Обратите внимание, что операторы заключены в символы `<#...#>`, а отдельные выражения — в символы `<#=...#>`. Дополнительные сведения см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

 Если вы записываете созданный код в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], директива `template` должна содержать атрибут `language="VB"`. Значение по умолчанию — `"C#"`.

## <a name="debugging-a-design-time-t4-text-template"></a>Отладка текстового шаблона времени разработки T4
 Отладка текстового шаблона

-   Вставьте строку `debug="true"` в директиву `template`. Например:

     `<#@ template debug="true" hostspecific="false" language="C#" #>`

-   Задайте точки останова в шаблоне таким же образом, как для обычного кода.

-   Выберите **отладить шаблон T4** в контекстном меню файла текстового шаблона в обозревателе решений.

 Шаблон запустится и будет останавливаться в точках останова. Вы можете проверить переменные и выполнить код пошагово в обычном режиме.

> [!TIP]
>  `debug="true"` более точно сопоставляет созданный код с текстовым шаблоном, вставляя в созданный код дополнительные директивы нумерации строк. Если опустить эту строку, точки останова могут останавливать выполнение в неверном состоянии.
>
>  Однако это выражение можно оставить в директиве шаблона, даже если вы не выполняете отладку. Это приведет к незначительному снижению производительности.

## <a name="generating-code-or-resources-for-your-solution"></a>Создание кода или ресурсов для решения
 Можно создать различающиеся файлы программ в зависимости от модели. Модель представляет собой источник входных данных, такой как база данных, файл конфигурации, модель UML, модель DSL или другой источник. Как правило, на основе одной модели создается несколько файлов программ. Для этого вы создаете файл шаблона для каждого создаваемого файла программы; для всех шаблонов задается чтение одной модели.

#### <a name="to-generate-program-code-or-resources"></a>Создание программного кода или ресурсов

1.  Измените директиву output, чтобы создать файл нужного типа, например .CS, .VB, .RESX или .XML.

2.  Вставьте код, который создаст нужный вам код решения. Например, если требуется создать три объявления поля Integer в классе, используйте код:

    ```csharp

              <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3.  Сохраните файл и проверьте созданный файл, который теперь содержит следующий код:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Создающий код и созданный текст
 При создании программного кода самое важное — не путать создающий код, который выполняется в шаблоне, и создаваемый код, который становится частью вашего решения. Языки этих двух частей не обязательно должны совпадать.

 Предыдущий пример имеет две версии. В одной версии создающий код написан на языке C#. В другой версии создающий код написан на языке Visual Basic. Однако создаваемый ими текст одинаков и является классом C#.

 Точно так же можно использовать шаблон [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] для создания кода на любом языке. Созданный текст не обязательно должен быть на определенном языке и вообще может не быть программным кодом.

### <a name="structuring-text-templates"></a>Структура текстовых шаблонов
 Как правило, рекомендуется разделять код шаблонов на две части.

-   Конфигурация или часть, отвечающая за сбор данных, которая задает значения переменных, но не содержит текстовые блоки. В предыдущем примере эта часть представлена кодом, инициализирующим `properties`.

     Ее иногда называют частью "модели", так как она создает хранимую модель и обычно считывает файл модели.

-   Часть, создающая текст, (`foreach(...){...}` в примере), которая использует значения переменных.

 Это разделение необязательно, однако оно упрощает чтение шаблона, делая менее сложной часть, которая включает текст.

## <a name="reading-files-or-other-sources"></a>Чтение файлов или других источников
 Чтобы получить доступ к файлу модели или базе данных, код шаблона может использовать сборки, такие как System.XML. Чтобы получить доступ к этим сборкам, необходимо вставить директивы, такие как следующие:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

 `assembly` Директива делает указанной сборки доступными код шаблона, так же, как в разделе ссылок проекта Visual Studio. Ссылку не требуется включать в System.dll, так как она создается автоматически. Директива `import` позволяет использовать типы, не используя полные имена, тем же способом, что и директива `using` в обычном файле программы.

 Например, после импорта **System.IO**, можно написать:

```csharp

      <# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>

```

### <a name="opening-a-file-with-a-relative-pathname"></a>Открытие файла с относительным путем
 Чтобы загрузить файл из расположения, относительного для текстового шаблона, можно использовать `this.Host.ResolvePath()`. Для использования this.Host необходимо задать выражение `hostspecific="true"` в `template`:

```
<#@ template debug="false" hostspecific="true" language="C#" #>

```

 Затем можно написать код, например:

```csharp
<# string fileName = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...

```

```vb
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>

```

 Кроме того, можно использовать `this.Host.TemplateFile`, определяющий имя текущего файла шаблона.

 Тип `this.Host` (в VB, `Me.Host`) — `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.

### <a name="getting-data-from-visual-studio"></a>Получение данных из Visual Studio
 Для использования служб, предоставляемых в Visual Studio задайте `hostSpecific` атрибут и нагрузки `EnvDTE` сборки. Затем можно использовать метод IServiceProvider.GetCOMService() для получения доступа к DTE и другим службам. Например:

```scr
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>

```

> [!TIP]
>  Текстовый шаблон выполняется в собственном домене приложений; доступ к службам предоставляется путем маршалинга. В этих обстоятельствах метод GetCOMService() надежнее, чем GetService().

## <a name="Regenerating"></a> Автоматическое повторное создание кода
 Как правило несколько файлов в решении Visual Studio создаются с помощью одной модели ввода. Каждый файл создается на основе своего собственного шаблона, но все шаблоны относятся к одной модели.

 Если изменяется исходная модель, необходимо перезапустить все шаблоны в решении. Чтобы сделать это вручную, выберите **преобразовать все шаблоны** на **построения** меню.

 Если вы установили Visual Studio пакет SDK моделирования, может иметь все шаблоны, преобразовывать автоматически при выполнении сборки. Для этого внесите изменения в файл проекта (CSPROJ или VBPROJ) в текстовом редакторе и добавьте следующие строки ближе к концу файла после любых других операторов `<import>`:

> [!NOTE]
> В Visual Studio 2017 пакет SDK преобразования текстового шаблона и Visual Studio пакет SDK моделирования устанавливаются автоматически при установке отдельных функций Visual Studio. Дополнительные сведения см. в разделе [этой записи блога](https://blogs.msdn.microsoft.com/visualstudioalm/2016/12/12/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

 Дополнительные сведения см. в разделе [создание кода в процессе построения](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Создание отчетов об ошибке
 Чтобы поместить ошибки и предупреждения в окне ошибок Visual Studio, можно использовать эти методы:

```
Error("An error message");
Warning("A warning message");
```

## <a name="Converting"></a> Преобразование существующего файла в шаблон
 Полезной возможностью шаблонов является то, что они очень похожи на создаваемые им файлы и включают некоторую часть программного кода. Это предполагает удобный способ создания шаблона. Сначала создайте обычный файл в качестве прототипа, такие как [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] файл, а затем постепенно вводите создающий код, изменяющий созданный файл.

#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Преобразование существующего файла в шаблон времени разработки

1.  В проект Visual Studio, добавьте файл типа, который вы хотите создать, например `.cs`, `.vb`, или `.resx` файл.

2.  Проверьте созданный файл, чтобы убедиться, что он работает.

3.  В обозревателе решений измените расширение имени файла для **.tt**.

4.  Проверьте следующие свойства **.tt** файла:

    |||
    |-|-|
    |**Пользовательский инструмент =**|**TextTemplatingFileGenerator**|
    |**Действие построения =**|**None**|

5.  Вставьте следующие строки в начало файла:

    ```
    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    ```

     Чтобы написать создающий код шаблона в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], задайте для атрибута `language` значение `"VB"` вместо `"C#"`.

     Задайте для атрибута `extension` значение расширения файла того типа, который требуется создать, например `.cs` `.resx` или `.xml`.

6.  Сохраните файл.

     Создается дочерний файл с заданным расширением. Его свойства будут правильными для данного типа файла. Например **действие при построении** свойство файла CS бы **компиляции**.

     Убедитесь, что созданный файл содержит то же содержимое, что и исходный.

7.  Определите часть файла, которую требуется изменять. Например часть, которая отображается только при соблюдении определенных условий, или повторяемая часть, или часть, в которой варьируются определенные значения. Вставьте создающий код. Сохраните файл и убедитесь, что дочерний файл создается правильно. Повторите этот шаг.

## <a name="guidelines-for-code-generation"></a>Рекомендации по созданию кода
 См. в разделе [рекомендации по текстовым шаблонам T4 записи](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Следующие шаги

|Следующий шаг|Раздел|
|---------------|-----------|
|Написание и отладка расширенного текстового шаблона с помощью кода, который использует вспомогательные функции, включенные файлы и внешние данные.|[Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)|
|Создание документов на основе шаблонов во время выполнения.|[Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Запуск создания текста за пределами Visual Studio.|[Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Преобразование данных в форме доменного языка.|[Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md)|
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>См. также

- [Рекомендации по написанию текстовых шаблонов T4](../modeling/guidelines-for-writing-t4-text-templates.md)
