---
title: Создание примечаний к функции параметров и возвращаемых значений | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c3a0cad60dc7867b31238669a612cdb0dac4097
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570014"
---
# <a name="annotating-function-parameters-and-return-values"></a>Создание примечаний к параметрам и возвращаемым значениям функций
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Аннотация параметров функции и возвращаемые значения](https://docs.microsoft.com/visualstudio/code-quality/annotating-function-parameters-and-return-values).  
  
В этой статье описываются типичные способы использования заметок параметры простой функции — скалярных величин и указатели на структуры и классы и в большинстве буферов.  В этой статье также показано распространенных шаблонов использования для заметки. Дополнительные заметки, относящиеся к функции, см. в разделе [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>Параметры-указатели  
 Для заметок в следующей таблице когда параметр-указатель помечается, анализатор сообщает об ошибке если указатель имеет значение null.  Это относится к указателям и для любого элемента, который указывает.  
  
 **Заметки и описания**  
  
-   `_In_`  
  
     Добавляет заметки к входные параметры, которые являются скалярные значения, структуры, указатели на структуры и т.п.  Явным образом может использоваться на простые скалярные значения.  Параметр должен быть допустимым в состоянии предварительной и не будет изменен.  
  
-   `_Out_`  
  
     Добавляет заметки к выходные параметры, которые являются скалярные значения, структуры, указатели на структуры и т.п.  Не устанавливайте это на объект, который не может возвращать значение — например, который передается по значению скалярного выражения.  Параметр не нужно быть допустимым в состоянии предварительной, но должен быть допустимым в состоянии после.  
  
-   `_Inout_`  
  
     Добавляет заметки к параметр, который будет изменен с помощью функции.  Он должен быть допустимым в состояние до и после состояния, но предполагается, что различные значения до и после вызова метода. Необходимо применить к изменяемое значение.  
  
-   `_In_z_`  
  
     Указатель на заканчивающуюся нулем строку, которая используется в качестве входных данных.  Строка должна быть допустимым в состоянии предварительной.  Варианты `PSTR`, который уже имеют корректными аннотациями, являются предпочтительными.  
  
-   `_Inout_z_`  
  
     Указатель на массив нуль-символом, который будет изменен.  Она должна быть допустимой, до и после вызова метода, но значение предполагается, что были изменены.  Знак завершения null могут быть перемещены, но может осуществляться только элементы до исходного нуль-символ.  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Указатель на массив, который считывается с помощью функции.  Массив имеет размер `s` элементов, каждый из которых должен быть допустимым.  
  
     `_bytes_` Вариант указывает размер в байтах вместо элементов. Используйте это только в том случае, если размер не могут быть выражены как элементы.  Например `char` строки будут использовать `_bytes_` вариант только в том случае, если аналогичное функцию, которая использует `wchar_t` бы.  
  
-   `_In_reads_z_(s)`  
  
     Указатель на массив, который заканчивается нулевым байтом и имеет известный размер. Элементы вплоть до нуль-символ — или `s` Если признак конца отсутствует значение null, должен быть допустимым в состоянии предварительной.  Если известно, размер в байтах, масштабировать `s` размером элемента.  
  
-   `_In_reads_or_z_(s)`  
  
     Указатель на массив, который заканчивается нулевым байтом или имеет известный размер, либо оба. Элементы вплоть до нуль-символ — или `s` Если признак конца отсутствует значение null, должен быть допустимым в состоянии предварительной.  Если известно, размер в байтах, масштабировать `s` размером элемента.  (Для `strn` семейства.)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Указатель на массив `s` элементов (ОТВ байт), которые будут записаны с помощью функции.  Элементы массива не имеют функционировал в состоянии предварительной, и количество элементов, которые являются допустимыми в состоянии после не определен.  Если существует примечаний к типу параметра, они применяются в состоянии после. Например, рассмотрим следующий код.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     В этом примере вызывающий объект предоставляет буфер `size` элементы для `p1`.  `MyStringCopy` делает некоторые из этих элементов допустимым. Что более важно `_Null_terminated_` заметки на `PWSTR` означает, что `p1` заканчивается нулевым байтом в состоянии после.  Таким образом число допустимых элементов, по-прежнему четко определено, но число конкретного элемента не является обязательным.  
  
     `_bytes_` Вариант указывает размер в байтах вместо элементов. Используйте это только в том случае, если размер не могут быть выражены как элементы.  Например `char` строки будут использовать `_bytes_` вариант только в том случае, если аналогичное функцию, которая использует `wchar_t` бы.  
  
-   `_Out_writes_z_(s)`  
  
     Указатель на массив `s` элементов.  Элементы, не обязаны быть допустимым в состоянии предварительной.  В состоянии после, элементы вверх по нуль-символ, который должен присутствовать, должен быть допустимым.  Если известно, размер в байтах, масштабировать `s` размером элемента.  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Указатель на массив, который является чтения и записи в функции.  Он имеет размер `s` элементов и может использоваться в состояния до и после.  
  
     `_bytes_` Вариант указывает размер в байтах вместо элементов. Используйте это только в том случае, если размер не могут быть выражены как элементы.  Например `char` строки будут использовать `_bytes_` вариант только в том случае, если аналогичное функцию, которая использует `wchar_t` бы.  
  
-   `_Inout_updates_z_(s)`  
  
     Указатель на массив, который заканчивается нулевым байтом и имеет известный размер. Элементы вверх по нуль-символ, который должен присутствовать, должен быть допустимым в состояние до и после состояния.  Значение в состоянии после принимается отличается от значения в состоянии предварительной; Эти сведения включают расположение знак завершения null. Если известно, размер в байтах, масштабировать `s` размером элемента.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Указатель на массив `s` элементов.  Элементы, не обязаны быть допустимым в состоянии предварительной.  В состоянии "после", элементы вплоть до `c`- й элемент должен быть допустимым.  Если известно, размер в байтах, масштабировать `s` и `c` размер элемента или используйте `_bytes_` вариант, который определяется следующим:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Другими словами, каждый элемент, который существует в буфере до `s` в состоянии предварительной находится в состоянии после параметра допустимым.  Пример:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Указатель на массив, который является чтения и записи функцией.  Он имеет размер `s` элементов, которые должны быть допустимым в состоянии предварительной, и `c` в состоянии после элементов должен быть допустимым.  
  
     `_bytes_` Вариант указывает размер в байтах вместо элементов. Используйте это только в том случае, если размер не могут быть выражены как элементы.  Например `char` строки будут использовать `_bytes_` вариант только в том случае, если аналогичное функцию, которая использует `wchar_t` бы.  
  
-   `_Inout_updates_z_(s)`  
  
     Указатель на массив, который заканчивается нулевым байтом и имеет известный размер. Элементы вверх по нуль-символ, который должен присутствовать, должен быть допустимым в состояние до и после состояния.  Значение в состоянии после принимается отличается от значения в состоянии предварительной; Эти сведения включают расположение знак завершения null. Если известно, размер в байтах, масштабировать `s` размером элемента.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Указатель на массив `s` элементов.  Элементы, не обязаны быть допустимым в состоянии предварительной.  В состоянии "после", элементы вплоть до `c`- й элемент должен быть допустимым.  Если известно, размер в байтах, масштабировать `s` и `c` размер элемента или используйте `_bytes_` вариант, который определяется следующим:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Другими словами, каждый элемент, который существует в буфере до `s` в состоянии предварительной находится в состоянии после параметра допустимым.  Пример:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Указатель на массив, который является чтения и записи функцией.  Он имеет размер `s` элементов, которые должны быть допустимым в состоянии предварительной, и `c` в состоянии после элементов должен быть допустимым.  
  
     `_bytes_` Вариант указывает размер в байтах вместо элементов. Используйте это только в том случае, если размер не могут быть выражены как элементы.  Например `char` строки будут использовать `_bytes_` вариант только в том случае, если аналогичное функцию, которая использует `wchar_t` бы.  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Указатель на массив, который является чтения и записи функцией размера `s` элементов. Определен как эквивалент:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Другими словами, каждый элемент, который существует в буфере до `s` в состоянии предварительной является допустимым состояния до и после.  
  
     `_bytes_` Вариант указывает размер в байтах вместо элементов. Используйте это только в том случае, если размер не могут быть выражены как элементы.  Например `char` строки будут использовать `_bytes_` вариант только в том случае, если аналогичное функцию, которая использует `wchar_t` бы.  
  
-   `_In_reads_to_ptr_(p)`  
  
     Указатель на массив, для которого выражение `p` — `_Curr_` (то есть `p` минус `_Curr_`) определен соответствующий языковым стандартом.  Элементы до `p` должен быть допустимым в состоянии предварительной.  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Указатель на массив, завершающаяся символом null, для которого выражение `p` — `_Curr_` (то есть `p` минус `_Curr_`) определен соответствующий языковым стандартом.  Элементы до `p` должен быть допустимым в состоянии предварительной.  
  
-   `_Out_writes_to_ptr_(p)`  
  
     Указатель на массив, для которого выражение `p` — `_Curr_` (то есть `p` минус `_Curr_`) определен соответствующий языковым стандартом.  Элементы до версии `p` больше не нужно быть допустимым в состоянии предварительной и должен быть допустимым в состоянии после.  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Указатель на массив, завершающаяся символом null, для которого выражение `p` — `_Curr_` (то есть `p` минус `_Curr_`) определен соответствующий языковым стандартом.  Элементы до версии `p` больше не нужно быть допустимым в состоянии предварительной и должен быть допустимым в состоянии после.  
  
## <a name="optional-pointer-parameters"></a>Необязательные операторы указателя параметров  
 Если содержит аннотацию параметра указатель `_opt_`, он указывает, что параметр может иметь значение null. В противном случае заметка выполняет совпадает с версией, не включает в себя `_opt_`. Ниже приведен список `_opt_` варианты заметок параметр указателя:  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Выходные параметры-указатели  
 Выходные параметры указателя требуют специальных нотации для устранения неоднозначности непустое значение для параметра и который указывает расположение.  
  
 **Заметки и описания**  
  
-   `_Outptr_`  
  
     Параметр не может иметь значение null, и в состоянии после расположения, который указывает, не может иметь значение null и должен быть допустимым.  
  
-   `_Outptr_opt_`  
  
     Параметр может иметь значение null, но в состоянии после расположения, который указывает, не может иметь значение null и должен быть допустимым.  
  
-   `_Outptr_result_maybenull_`  
  
     Параметр не может иметь значение null, и в состоянии после который указывает расположение может иметь значение null.  
  
-   `_Outptr_opt_result_maybenull_`  
  
     Параметр может иметь значение null, и в состоянии после который указывает расположение может иметь значение null.  
  
 В следующей таблице дополнительные подстроки будут вставлены в имя заметки для дальнейшего уточнения значение заметки.  Различных подстрок, `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, и `_to_`.  
  
> [!IMPORTANT]
>  Если интерфейс, который как добавлять заметки COM, используйте форму COM этих заметок. Не используйте заметки COM с помощью любого другого типа интерфейса.  
  
 **Заметки и описания**  
  
-   `_Outptr_result_z_`  
  
     `_Outptr_opt_result_z_`  
  
     `_Outptr_result_maybenull_z_`  
  
     `_Ouptr_opt_result_maybenull_z_`  
  
     Возвращенный указатель имеет `_Null_terminated_` заметки.  
  
-   `_COM_Outptr_`  
  
     `_COM_Outptr_opt_`  
  
     `_COM_Outptr_result_maybenull_`  
  
     `_COM_Outptr_opt_result_maybenull_`  
  
     Возвращенный указатель имеет семантики COM и поэтому объемом `_On_failure_` после условием, что возвращенный указатель имеет значение null.  
  
-   `_Outptr_result_buffer_(s)`  
  
     `_Outptr_result_bytebuffer_(s)`  
  
     `_Outptr_opt_result_buffer_(s)`  
  
     `_Outptr_opt_result_bytebuffer_(s)`  
  
     Возвращаемый указатель указывает на допустимый буфер размера `s` элементов или байт.  
  
-   `_Outptr_result_buffer_to_(s, c)`  
  
     `_Outptr_result_bytebuffer_to_(s, c)`  
  
     `_Outptr_opt_result_buffer_to_(s,c)`  
  
     `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
     Возвращаемый указатель указывает на буфер размером `s` элементов или байт, из которых первый `c` являются допустимыми.  
  
 Определенные соглашения в интерфейс предположить, что выходные параметры являются обнулить в случае сбоя.  За исключением явно кода модели COM форм, в следующей таблице являются предпочтительными.  Для кода модели COM используйте соответствующими формами COM, перечисленных в предыдущем разделе.  
  
 **Заметки и описания**  
  
-   `_Result_nullonfailure_`  
  
     Изменяет другие аннотации. Результат будет присвоено значение null, если функция завершается с ошибкой.  
  
-   `_Result_zeroonfailure_`  
  
     Изменяет другие аннотации. Результат присваивается нулевое значение, если функция завершается с ошибкой.  
  
-   `_Outptr_result_nullonfailure_`  
  
     Возвращаемый указатель указывает на допустимый буфер, если функция выполняется успешно, или значение null, если функция завершается с ошибкой. Эта заметка является обязательным параметра.  
  
-   `_Outptr_opt_result_nullonfailure_`  
  
     Возвращаемый указатель указывает на допустимый буфер, если функция выполняется успешно, или значение null, если функция завершается с ошибкой. Эта заметка является для необязательного параметра.  
  
-   `_Outref_result_nullonfailure_`  
  
     Возвращаемый указатель указывает на допустимый буфер, если функция выполняется успешно, или значение null, если функция завершается с ошибкой. Эта заметка является для ссылочного параметра.  
  
## <a name="output-reference-parameters"></a>Выходными ссылочными параметрами  
 Ссылочный параметр обычно используется для выходных параметров.  Для простых выходными ссылочными параметрами — например, `int&`—`_Out_` обеспечивает правильное семантику.  Тем не менее, в том случае, когда выходное значение является указателем, например `int *&`— эквивалент указатель заметок, такие как `_Outptr_ int **` не обеспечивают правильное семантику.  Чтобы кратко выразить семантика выходными ссылочными параметрами для типов указателей, использование этих составных заметок:  
  
 **Заметки и описания**  
  
-   `_Outref_`  
  
     Результат должен быть допустимым в после состоянии и не может иметь значение null.  
  
-   `_Outref_result_maybenull_`  
  
     Результат должен быть допустимым в состоянии после, но может иметь значение null в состоянии после.  
  
-   `_Outref_result_buffer_(s)`  
  
     Результат должен быть допустимым в после состоянии и не может иметь значение null. Указывает на допустимый буфер размером `s` элементов.  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     Результат должен быть допустимым в после состоянии и не может иметь значение null. Указывает на допустимый буфер размером `s` байт.  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     Результат должен быть допустимым в после состоянии и не может иметь значение null. Указывает буфер `s` элементы, из которых первый `c` являются допустимыми.  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     Результат должен быть допустимым в после состоянии и не может иметь значение null. Указывает буфер `s` байт, из которых первый `c` являются допустимыми.  
  
-   `_Outref_result_buffer_all_(s)`  
  
     Результат должен быть допустимым в после состоянии и не может иметь значение null. Указывает на допустимый буфер размером `s` допустимых элементов.  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     Результат должен быть допустимым в после состоянии и не может иметь значение null. Указывает на допустимый буфер `s` байтов, допустимых элементов.  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     Результат должен быть допустимым в состоянии после, но может иметь значение null в состоянии после. Указывает на допустимый буфер размером `s` элементов.  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Результат должен быть допустимым в состоянии после, но может иметь значение null в состоянии после. Указывает на допустимый буфер размером `s` байт.  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Результат должен быть допустимым в состоянии после, но может иметь значение null в состоянии после. Указывает буфер `s` элементы, из которых первый `c` являются допустимыми.  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Результат должен быть допустимым в состоянии после, но может иметь значение null в состоянии отправки. Указывает буфер `s` байт, из которых первый `c` являются допустимыми.  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     Результат должен быть допустимым в состоянии после, но может иметь значение null в состоянии отправки. Указывает на допустимый буфер размером `s` допустимых элементов.  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Результат должен быть допустимым в состоянии после, но может иметь значение null в состоянии отправки. Указывает на допустимый буфер `s` байтов, допустимых элементов.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращаемое значение функции напоминает `_Out_` параметра, но находится в другой уровень de-reference, и не нужно рассмотреть понятие указатель на результат.  Следующие заметки, возвращаемое значение является объектом с заметками, скалярным, указатель на структуру или указатель на буфер. Эти заметки имеют ту же семантику, что и соответствующий `_Out_` заметки.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Другие распространенные аннотации  
 **Заметки и описания**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Параметр, поле или результат находится в диапазоне (включительно) из `low` для `hi`.  Эквивалентно `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` , применяемый к аннотированному объекту вместе с соответствующие условия предварительно состояния рабочих процессов и после.  
  
    > [!IMPORTANT]
    >  Несмотря на то, что имена содержат «in» и «Исходящие», семантика `_In_` и `_Out_` сделать **не** применить эти заметки.  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Именно это значение с заметками `expr`.  Эквивалентно `_Satisfies_(_Curr_ == expr)` , применяемый к аннотированному объекту вместе с соответствующие условия предварительно состояния рабочих процессов и после.  
  
-   `_Struct_size_bytes_(size)`  
  
     Применяется к объявлению структуры или класса.  Указывает, что допустимый объект этого типа может быть больше объявленного типа, с числом байтов, которые получают по `size`.  Пример:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Размер буфера в байтах параметра `pM` типа `MyStruct *` затем принимается:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Связанные ресурсы  
 [Блог команды анализа кода](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>См. также  
 [Использование аннотаций SAL для сокращения количества дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Основные сведения о SAL](../code-quality/understanding-sal.md)   
 [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)   
 [Аннотация структур и классов](../code-quality/annotating-structs-and-classes.md)   
 [Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)   
 [Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Встроенные функции](../code-quality/intrinsic-functions.md)   
 [Рекомендации и примеры](../code-quality/best-practices-and-examples-sal.md)



