---
title: Флаги командной строки компилятора VSCT | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19ebf1713c2a0d42b1269befa3bea28d4dc0309b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568786"
---
# <a name="vsct-compiler-command-line-flags"></a>Флаги командной строки компилятора VSCT
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [флаги командной строки компилятора VSCT](https://docs.microsoft.com/visualstudio/extensibility/internals/vsct-compiler-command-line-flags).  
  
Компилятора таблицы команд Visual Studio (VSCT) предоставляет параметры командной строки для обеспечения успешной компиляции vsct-файлы.  
  
## <a name="command-line-parameters"></a>Параметры командной строки  
 Чтобы просмотреть основную справку VSCT из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **команда** окно, перейдите к *путь установки Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ папку и введите:  
  
```  
vsct /?  
```  
  
 Эта команда возвращает:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Символы - (дефис) и / (косая черта) являются оба принятые нотации, указывающие параметры командной строки.  
  
 Ниже приведены допустимые флаги и разъяснения к ним.  
  
|Параметр|Описание|  
|------------|-----------------|  
|-D|Укажите любые дополнительные определенные символы.|  
|-I|Указать, что дополнительные пути поиска включаемых файлов, которые должны использоваться при разрешении ссылок на файлы.|  
|-L|Укажите <xref:System.Globalization.CultureInfo> имя языка и региональных параметров, например «en US».|  
|-E|Возвращает объектов C# в указанного пространства имен для элементов команды, за которым следует [C&#124;H&#124;N]:*filename*где C = C#, H = заголовок C++, N = пространство имен. Пространство имен является обязательным для C#.|  
|-v|Подробные выходные данные.|  
  
 Переключатель -L указывает компилятору на необходимость выбрать группу строк для получения двоичного cto-файла, соответствующее заданной <xref:System.Globalization.CultureInfo> имя языка и региональных параметров. Имя заданного языка и региональных параметров должно соответствовать атрибуту языка из одного или нескольких [элемент Strings](../../extensibility/strings-element.md) в vsct-файле. Элемент строки имеет атрибут не языка, наследуется от содержащего [элемент CommandTable](../../extensibility/commandtable-element.md).  
  
 Vsct-файл может иметь несколько элементов строк, и может иметь другой атрибут языка. Глобализация достигается, запустив компилятора VSCT несколько раз и изменив переключатель -L для каждого имени языка и региональных параметров.  
  
 Если имя языка и региональных параметров, заданное параметром -L не соответствует атрибуте Language элемента любой строки, компилятор будет пытаться соответствует язык, а не регион. Например если не удается найти «en US», компилятор попробует вместо «en». После неудачной будет предпринята текущий язык и региональные параметры операционной системы. После неудачной компиляции на первый элемент строки, найденные.  
  
 Создает файл заголовка C-стиля, содержащий символы, используемые таблицы команд или создает файл C#, содержащий объекты для символов, команда может использовать параметр -E.  
  
 -D и – я коммутаторы иметь синтаксис препроцессора Cl.exe C флагов, которые имеют одинаковые имена. – D для возможности расширения на основе XML используются термины, в формате X = Y \<определенные > тесты в `Condition` атрибуты. — Я пути включения, используются для разрешения \<Include >, \<Extern > и \<точечного рисунка > ссылки на файлы. Дополнительные сведения см. в разделе [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Компилятора VSCT также может декомпилировать существует ранее построенный двоичный файл. Для этого, передать двоичный файл для \<infile >.   Если двоичный файл был создан с помощью компилятора VSCT, окажется внедренных символов и будет выдавать выходные данные с символические имена в \<символы > раздел выходных данных. Если двоичный файл был создан компилятором CTC, выходные данные будут содержать фактические идентификаторы GUID и идентификаторы. Если в той же папке, как двоичный файл входной файл *.ctsym, созданным текущих версиях Ctc.exe, символы будут загружаться из этого файла и используется для вывода.  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Command Table (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md)   
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

