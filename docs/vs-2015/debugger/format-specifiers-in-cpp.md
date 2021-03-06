---
title: Format Specifiers in C++ | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 45
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d495fff6848a8d62be5a4471ee6a036cf9054fff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572441"
---
# <a name="format-specifiers-in-c"></a>Определители формата в C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [описатели формата в C++](https://docs.microsoft.com/visualstudio/debugger/format-specifiers-in-cpp).  
  
С помощью описателей формата можно изменить формат, в котором значение отображается в окне **Контрольные значения** .  
  
 Описатели формата можно также использовать в окне **интерпретации** , окне **команд** и даже в окнах исходного кода. Если вы приостановите выполнение на выражении в одном из этих окон, результат отобразится в подсказке по данным. В подсказке по данным указывается описатель формата.  
  
> [!NOTE]
>  Отладчик машинного кода Visual Studio переведен на новое ядро отладки. В рамках этого изменения был добавлен ряд новых описателей формата, а некоторые старые описатели были удалены. Прежний отладчик все еще используется при отладке взаимодействия (то есть смешанной отладке машинного и управляемого кода) с использованием C++/CLI. В подразделах этого раздела показаны описатели формата для каждого ядра отладки.  
>   
>  -   [Описатели формата](#BKMK_Visual_Studio_2012_format_specifiers) рассматриваются описатели формата в новом ядре отладки.  
> -   [Описатели формата для отладки взаимодействия с использованием C++/CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) рассматриваются описатели формата в прежнем ядре отладки.  
  
## <a name="using-format-specifiers"></a>Использование описателей формата  
 Предположим, что имеется следующий код:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Добавьте переменную `my_var1` в окно **Контрольные значения** (во время отладки выберите **Отладка &gt; Окна &gt; Контрольные значения &gt; Контрольные значения 1**) и задайте шестнадцатеричный вывод (в окне **Контрольные значения** щелкните переменную правой кнопкой мыши и выберите пункт **Шестнадцатеричный вывод**). Теперь в окне "Контрольные значения" показано значение 0x0065. Чтобы представить это значение в символьном, а не целочисленном формате, в столбце "Имя" после имени переменной добавьте описатель символьного формата **, c**. В столбце **Значение** теперь отображается значение **101 'e'**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Описатели формата  
 В приведенных ниже таблицах показаны описатели формата, которые можно использовать в Visual Studio. Описатели, выделенные полужирным шрифтом, не поддерживаются для отладки взаимодействия с использованием C++/CLI.  
  
|Описатель|Формат|Исходное контрольное значение|Отображаемое значение|  
|---------------|------------|--------------------------|---------------------|  
|d|Десятичное целое число|0x00000066|102|  
|o|Восьмеричное целое число без знака|0x00000066|000000000146|  
|x<br /><br /> **h**|шестнадцатеричное целое число|102|0xcccccccc|  
|X<br /><br /> **H**|шестнадцатеричное целое число|102|0xcccccccc|  
|c|одиночный символ|0x0065, c|101 'e'|  
|s|const char* string|\<расположение > «hello world»|"Здравствуй, мир!"|  
|**sb**|const char* string|\<расположение > «hello world»|Здравствуй, мир!|  
|s8|const char* string|\<расположение > «hello world»|"Здравствуй, мир!"|  
|**s8b**|const char* string|\<расположение > «hello world»|"Здравствуй, мир!"|  
|su|const wchar_t * const<br /><br /> char16_t\* строки|\<расположение > L «hello world»|L"Здравствуй, мир!"<br /><br /> u"Здравствуй, мир!"|  
|sub|const wchar_t * const<br /><br /> char16_t\* строки|\<расположение > L «hello world»|Здравствуй, мир!|  
|bstr|Строка BSTR|\<расположение > L «hello world»|L"Здравствуй, мир!"|  
|**s32**|Строка UTF-32|\<расположение > U «hello world»|U"Здравствуй, мир!"|  
|**s32b**|Строка UTF-32 (без кавычек)|\<расположение > U «hello world»|Здравствуй, мир!|  
|**en**|перечисление|Суббота(6)|Суббота|  
|**hv**|Тип указателя — указывает на то, что проверяемое значение указателя является результатом выделения кучи для массива, например `new int[3]`.|\<расположение > {\<первый элемент >}|\<расположение > {\<первый элемент >, \<второй элемент >,...}|  
|**na**|Подавляет адрес указателя на объект в памяти.|\<расположение >, {элемент = значение …}|{элемент=значение…}|  
|**nd**|Отображает только данные базового класса без учета производных классов.|`(Shape*) square` включает данные базового и производных классов|Отображает только данные базового класса|  
|hr|Код ошибки HRESULT или Win32 (В настоящее время отладчик автоматически расшифровывает коды HRESULT, и в этих случаях данный спецификатор не требуется.)|S_OK|S_OK|  
|wc|Флаг класса Window|0x0010|WC_DEFAULTCHAR|  
|wm|Номера сообщений Windows|16|WM_CLOSE|  
|!|Формат raw (необработанные данные), все настройки представлений типов данных не учитываются|\<настроить представление >|4|  
  
> [!NOTE]
>  Если присутствует описатель формата **hv** , отладчик пытается определить длину буфера и отобразить соответствующее число элементов. Так как отладчик не всегда может точно определить размер буфера массива, по возможности следует использовать описатель размера `(pBuffer,[bufferSize])` . Описатель формата **hv** предназначен для ситуаций, в которых размер буфера нельзя определить сразу.  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Описатели размера для указателей как массивов  
 Если имеется указатель на объект, который требуется просмотреть в виде массива, можно использовать целое число или выражение для указания числа элементов массива.  
  
|Описатель|Формат|Исходное контрольное значение|Отображаемое значение|  
|---------------|------------|---------------------------|---------------------|  
|n|Десятичное или **шестнадцатеричное** целое число|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Отображает `pBuffer` как массив из 32 элементов.|  
|**[exp]**|Допустимое выражение C++, результатом которого является целое число.|pBuffer,[bufferSize]|Отображает pBuffer как массив `bufferSize` элементов.|  
|**expand(n)**|Допустимое выражение C++, результатом которого является целое число.|pBuffer, expand(2)|Отображает третий элемент  `pBuffer`.|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Описатели формата для отладки взаимодействия с использованием C++/CLI  
 Описатели, выделенные **полужирным** шрифтом, поддерживаются только при отладке машинного кода и кода C++/CLI.  
  
|Описатель|Формат|Исходное контрольное значение|Отображаемое значение|  
|---------------|------------|--------------------------|---------------------|  
|**d,i**|Десятичное целое число со знаком|0xF000F065|-268373915|  
|**u**|Десятичное целое число без знака|0x0065|101|  
|o|Восьмеричное целое число без знака|0xF065|0170145|  
|x,X|шестнадцатеричное целое число|61541|0x0000f065|  
|**l,h**|Префикс длинного или короткого формата для спецификаторов d, i, u, o, x и X|00406042|0x0c22|  
|**f**|Число с плавающей запятой со знаком|(3./2.), f|1.500000|  
|**e**|Число в экспоненциальном представлении со знаком|(3.0/2.0)|1,500000e+000|  
|**g**g|Число с плавающей запятой со знаком или число в экспоненциальном представлении со знаком, в зависимости от того, какой формат короче|(3.0/2.0)|1.5|  
|c|одиночный символ|\<расположение >|101 'e'|  
|s|const char*|\<расположение >|"Здравствуй, мир!"|  
|su|const wchar_t*<br /><br /> const char16_t\*|\<расположение >|L"Здравствуй, мир!"|  
|sub|const wchar_t*<br /><br /> const char16_t\*|\<расположение >|Здравствуй, мир!|  
|s8|const char*|\<расположение >|"Здравствуй, мир!"|  
|hr|Код ошибки HRESULT или Win32 (В настоящее время отладчик автоматически расшифровывает коды HRESULT, и в этих случаях данный спецификатор не требуется.)|S_OK|S_OK|  
|wc|Флаг класса Window|0x00000040,|WC_DEFAULTCHAR|  
|wm|Номера сообщений Windows|0x0010|WM_CLOSE|  
|!|Формат raw (необработанные данные), все настройки представлений типов данных не учитываются|\<настроить представление >|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Описатели формата адресов памяти при отладке взаимодействия с использованием C++/CLI  
 В следующей таблице содержатся символы, используемые для обозначения форматов представления адресов памяти. Спецификатор адреса памяти можно использовать для любого значения или выражения, возвращающего адрес ячейки памяти.  
  
|Символ|Формат|Исходное контрольное значение|Отображаемое значение|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 знака ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 байт в шестнадцатеричном формате и затем 16 знаков ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mb**|16 байт в шестнадцатеричном формате и затем 16 знаков ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mw**|8 слов|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 двойных слова|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 учетверенных слова|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2-байтовые знаки (Юникод)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Описатель размера для указателей как массивов при отладке взаимодействия с использованием C++/CLI  
 Если имеется указатель на объект, который требуется просмотреть в виде массива, можно использовать целое число для указания числа элементов массива.  
  
|класса хранения|Формат|Выражение|Отображаемое значение|  
|---------------|------------|----------------|---------------------|  
|n|Десятичное целое число|pBuffer[32]|Отображает `pBuffer` как массив из 32 элементов.|





