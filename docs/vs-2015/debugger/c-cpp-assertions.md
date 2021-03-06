---
title: Утверждения C / C++ | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce168764f18d85cce1d373bf509f63bfb1e6923d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559559"
---
# <a name="cc-assertions"></a>Утверждения C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [утверждения C/C++](https://docs.microsoft.com/visualstudio/debugger/c-cpp-assertions).  
  
Оператор утверждения задает условие, которое должно выполняться на определенном этапе работы программы. Если это условие не соблюдается, утверждение признается ложным, выполнение программы прерывается и [диалоговое окно](../debugger/assertion-failed-dialog-box.md) отображается.  
  
 Язык Visual C++ поддерживает операторы утверждений, основанные на следующих конструкциях:  
  
-   Утверждения MFC для программ MFC.  
  
-   [ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) для программ, использующих ATL.  
  
-   Утверждения CRT для программ, использующих библиотеку времени выполнения C.  
  
-   ANSI [функция assert](http://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40) для других программ C/C++.  
  
 Можно использовать утверждения для перехвата логических ошибок, проверки результатов операции и условий ошибки теста, которые должны были быть обработаны.  
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 [Как работают утверждения](#BKMK_How_assertions_work)  
  
 [Утверждения в сборках отладки и выпуска](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [Побочные эффекты использования утверждений](#BKMK_Side_effects_of_using_assertions)  
  
 [Утверждения CRT](#BKMK_CRT_assertions)  
  
 [Утверждения MFC](#BKMK_MFC_assertions)  
  
-   [MFC ASSERT_VALID и CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [Ограничения AssertValid](#BKMK_Limitations_of_AssertValid)  
  
 [С помощью проверочных утверждений](#BKMK_Using_assertions)  
  
-   [Перехват логических ошибок](#BKMK_Catching_logic_errors)  
  
-   [Проверка результатов](#BKMK_Checking_results_)  
  
-   [Поиск необработанных ошибок](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a> Как работают утверждения  
 Когда отладчик останавливается из-за утверждения MFC или библиотеки времени выполнения C, при наличии исходного кода отладчик перемещается к той точке в исходном файле, где сработало утверждение. Это сообщение появляется в обеих [окно вывода](../ide/reference/output-window.md) и **ложности** диалоговое окно. Вы можете скопировать сообщение из **вывода** окно в текстовое окно, если вы хотите сохранить его для дальнейшего использования. **Вывода** окно может содержать другие сообщения об ошибках. Следует тщательно проверять эти сообщения, потому что они могут объяснить причину сбоя утверждения.  
  
 Используйте утверждения для обнаружения ошибок во время разработки. Как правило, следует использовать одно утверждение для каждого предположения. Например, если предполагается, что аргумент не равен NULL, используйте утверждение для проверки этого предположения.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Утверждения в сборках отладки и выпуска  
 Операторы утверждений компилируются, только если определен `_DEBUG`. В противном случае компилятор рассматривает утверждения как операторы со значением NULL. Поэтому операторы утверждения не накладывают дополнительной нагрузки и не вызывают снижения производительности в итоговом выпуске программы и позволяют избежать использования директив `#ifdef`.  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a> Побочные эффекты использования утверждений  
 При добавлении утверждения в код следует убедиться, что это не вызовет побочных эффектов. Например, рассмотрим следующее утверждение, изменяющее значение `nM`.  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 Поскольку выражение `ASSERT` не оценивается в окончательной версии программы, `nM` будет иметь различные значения в отладочной версии и в окончательной версии. Чтобы избежать этой проблемы в MFC, можно использовать [VERIFY](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) макрос вместо `ASSERT`.  `VERIFY` Вычисляет выражение во всех версиях, но не проверяет результат в окончательной версии.  
  
 Следует быть особенно осторожным при вызовах функций в операторах утверждений, так как оценка функции может вызвать неожиданные побочные эффекты.  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY` вызывает `myFnctn` как в отладочной, так и в окончательной версии, поэтому им можно свободно пользоваться. Однако использование `VERIFY` в окончательной версии выпуска влечет дополнительную нагрузку в виде ненужного вызова функции.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a> Утверждения CRT  
 CRTDBG. Файл заголовка [макросы _ASSERT и _ASSERTE](http://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36) для проверки утверждения.  
  
|Макрос|Результат|  
|-----------|------------|  
|`_ASSERT`|Если заданное выражение оценивается как FALSE, то результатом будет имя файла и номер строки `_ASSERT`.|`_ASSERTE`|  
|`_ASSERTE`|Так же, как и `_ASSERT`, плюс строковое представление выражения, для которого было добавлено утверждение.|  
  
 `_ASSERTE` более эффективен, так как он выводит выражение, принявшее значение FALSE. Этого действия может быть достаточно для распознавания проблемы без обращения к исходному коду. Однако отладочная версия приложения будет содержать строковую константу для каждого выражения, обрабатываемого `_ASSERTE`. При использовании нескольких макросов `_ASSERTE` эти строковые выражения могут требовать значительного количества памяти. Если это вызывает проблемы, то для экономии памяти используйте `_ASSERT`.  
  
 Если `_DEBUG` определен, макрос `_ASSERTE` определяется следующим образом:  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 Если утверждаемое выражение оценивается как FALSE, [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) вызывается для отчета о ложности утверждения (используя диалоговое окно сообщения по умолчанию). Если вы выберете **повторите** в диалоговом окне сообщения `_CrtDbgReport` возвращает значение 1, и `_CrtDbgBreak` вызывает отладчик с помощью `DebugBreak`.  
  
### <a name="checking-for-heap-corruption"></a>Проверка целостности кучи  
 В следующем примере используется [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765) для проверки кучи:  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### <a name="checking-pointer-validity"></a>Проверка допустимости указателя  
 В следующем примере используется [_CrtIsValidPointer](http://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa) для проверки, допустима ли данная область памяти для чтения или записи.  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 В следующем примере используется [_CrtIsValidHeapPointer](http://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5) для проверки, указывает ли указатель на буфер, в локальной куче (которая создается и управляется экземпляром библиотеки времени выполнения C — DLL-ФАЙЛ может иметь свой собственный экземпляр библиотеки, и Таким образом свою собственную кучу, вне кучи приложения). Это утверждение перехватывает не только пустые или выходящие за пределы области адреса, но и указатели на статические переменные, переменные стека и другую нелокальную память.  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### <a name="checking-a-memory-block"></a>Проверка блока памяти  
 В следующем примере используется [_CrtIsMemoryBlock](http://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273) чтобы убедиться, что блок памяти в локальной куче и имеет тип допустимым.  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a> Утверждения MFC  
 MFC определяет [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) макрос для проверки утверждения. Здесь также определяются методы `MFC ASSERT_VALID` и `CObject::AssertValid` для проверки внутреннего состояния объекта, производного от `CObject`.  
  
 Если аргумент MFC-макроса `ASSERT` равняется нулю или значению false, макрос останавливает выполнение программы и предупреждает пользователя; в противном случае выполнение продолжается.  
  
 Когда утверждение ложно, диалоговое окно сообщения отображает имя исходного файла и номер строки утверждения. Если выбрать "Повторить" в диалоговом окне поле, вызов [AfxDebugBreak](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) прерывает выполнение программы к отладчику. В этот момент можно для определения причины ложности утверждения проверить стек вызовов и использовать другие функции отладчика. Если вы включили [Just-in-time отладки](../debugger/just-in-time-debugging-in-visual-studio.md)и отладчик еще не запущен, диалоговое окно можно запустить отладчик.  
  
 Следующий пример показывает, как использовать `ASSERT` для проверки значения, возвращаемого следующей функцией:  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 Можно использовать ASSERT с [IsKindOf](http://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6) функции использовать проверку типов аргументов функции:  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 Макрос `ASSERT` не создает никакого кода в окончательной версии. Если необходимо вычислить выражение в окончательной версии, используйте [VERIFY](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) макрос вместо ASSERT.  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID и CObject::AssertValid  
 [CObject::AssertValid](http://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157) метод предоставляет внутреннее состояние объекта проверок во время выполнения. Переопределение функции `AssertValid` при получении класса из `CObject` позволяет сделать данный класс более надежным, хотя такое переопределение необязательно. Функция `AssertValid` должна выполнить утверждения для всех переменных-членов объекта, чтобы подтвердить наличие только допустимых значений. Например, с ее помощью следует проверить, что переменные-члены указателя не равны NULL.  
  
 В следующем примере показан способ объявления функции `AssertValid`:  
  
```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
  
```  
  
 При переопределении `AssertValid` перед выполнением собственных проверок вызовите версию `AssertValid` базового класса. Затем примените макрос ASSERT для проверки членов, уникальных для данного производного класса, как показано ниже:  
  
```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  
  
    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
  
```  
  
 Если какие-то из переменных-членов содержат объекты, можно применить макрос `ASSERT_VALID` для проверки их внутренней допустимости (если их классы переопределяют `AssertValid`).  
  
 Например, рассмотрим класс `CMyData`, какие магазины [CObList](http://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca) в одном из своих переменных-членов. В переменной `CObList`, `m_DataList`, хранится коллекция объектов `CPerson`. Сокращенное объявление `CMyData` выглядит следующим образом:  
  
```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
  
```  
  
 Переопределение `AssertValid` в `CMyData` выглядит следующим образом:  
  
```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
  
```  
  
 `CMyData` использует механизм `AssertValid` для проверки допустимости объектов, хранящихся в его членах данных. Метод переопределения `AssertValid` из `CMyData` вызывает макрос `ASSERT_VALID` для собственной переменной-члена m_pDataList.  
  
 Проверка допустимости на этом уровне не останавливается, поскольку класс `CObList` тоже переопределяет `AssertValid`. Это переопределение выполняет добавочную проверку допустимости внутреннего состояния списка. Таким образом, тест допустимости для объекта `CMyData` вызывает дополнительную проверку внутреннего состояния сохраненного объекта списка `CObList`.  
  
 Приложив еще немного усилий, точно так же можно добавить тесты допустимости для объектов `CPerson`, хранящихся в списке. Можно создать класс `CPersonList` из `CObList` и переопределить `AssertValid`. В переопределении можно вызвать `CObject::AssertValid` и затем итерировать все элементы списка, вызывая `AssertValid` по каждому объекту `CPerson` в списке. Класс `CPerson`, показанный в начале этого раздела, содержит уже переопределенный `AssertValid`.  
  
 Это очень мощный механизм для построения отладки. А при построении окончательной версии этот механизм автоматически отключается.  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a> Ограничения AssertValid  
 Сработавшее утверждение показывает, что объект определенно является плохим, и выполнение будет остановлено. Однако отсутствие утверждений указывает только то, что проблемы не найдены, но не гарантирует качество объекта.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a> С помощью проверочных утверждений  
  
###  <a name="BKMK_Catching_logic_errors"></a> Перехват логических ошибок  
 Утверждение может быть основано на условии, которое должно быть истинным в соответствии с логикой программы. Пока не возникает логическая ошибка, утверждение не срабатывает.  
  
 Например, предположим, что моделируются молекулы газа в контейнере, и переменная `numMols` предоставляет их общее количество. Это число не может быть меньше нуля, поэтому можно вставить MFC-оператор наподобие следующего:  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 Или же вставить подобное CRT-утверждение:  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 Если программа работает корректно, эти операторы ничего не делают. Если логическая ошибка вызывает `numMols` стало меньше нуля, однако утверждение останавливает выполнение программы и отображает [сбой диалоговое окно подтверждения](../debugger/assertion-failed-dialog-box.md).  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a> Проверка результатов  
 Утверждения полезны для проверки операций, результаты которых не очевидны при беглом просмотре.  
  
 Рассмотрим следующий код, в котором для обновления переменной `iMols` используется содержимое связанного списка, на который указывает `mols`:  
  
```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  
  
 Количество молекул, вычисляемое с помощью переменной `iMols`, всегда должно быть меньше или равно общему количеству молекул — `numMols`.  При поверхностном взгляде на цикл это сложно определить, поэтому после цикла для проверки этого условия и применяется оператор утверждения.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a> Поиск необработанных ошибок  
 Утверждения также можно применять для выявления причин ошибок в том месте кода, где эти ошибки должны обрабатываться. В следующем примере графическая программа возвращает код ошибки или ноль при успешном завершении.  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 Если код, обрабатывающий ошибку, работает правильно, ошибка будет обработана и `myErr` сбросится в ноль, не доходя до утверждения. Если `myErr` имеет другое значение, сработает утверждение, программа остановится и [сбой диалоговое окно подтверждения](../debugger/assertion-failed-dialog-box.md) отображается.  
  
 Однако операторы утверждения все же не заменяют кода обработки ошибок. Следующий пример показывает, как оператор утверждения может привести к проблемам в окончательной версии программы:  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 Этот код основан на операторе утверждения для обработки условия ошибки. В результате любой код ошибки, возвращенный `myGraphRoutine`, не будет обработан в окончательном выпуске программы.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Утверждения в управляемом коде](../debugger/assertions-in-managed-code.md)



