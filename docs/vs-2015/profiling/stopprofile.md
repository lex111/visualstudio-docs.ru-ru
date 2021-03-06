---
title: StopProfile | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 326ed9afa9d277babde5cda99ba5640f6d66bd98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571292"
---
# <a name="stopprofile"></a>StopProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [StopProfile](https://docs.microsoft.com/visualstudio/profiling/stopprofile).  
  
Функция `StopProfile` устанавливает счетчик в значение 0 (включено) для указанного уровня профилирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Параметры  
 `Level`  
  
 Указывает уровень профилирования, к которому можно применить сбор данных по производительности. Для указания одного из трех уровней, к которому можно применить сбор данных по производительности, следует использовать представленные ниже перечислители **PROFILE_CONTROL_LEVEL**:  
  
|Перечислитель|Описание|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Установка глобального уровня оказывает влияние на все процессы и потоки при выполнении профилирования.|  
|PROFILE_PROCESSLEVEL|Установка уровня процесса оказывает влияние на все потоки, являющиеся частью указанного процесса.|  
|PROFILE_THREADLEVEL|Установка уровня профилирования потока влияет на заданный поток.|  
  
 `dwId`  
  
 Идентификатор процесса или потока, созданный системой.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Функция информирует об успехе или неудаче с помощью перечисления **PROFILE_COMMAND_STATUS**. Может возвращаться одно из следующих значений:  
  
|Перечислитель|Описание|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Идентификатор элемента профилирования не существует.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Заданный уровень профилирования не существует.|  
|PROFILE_ERROR_MODE_NEVER|На момент вызова функции был установлен режим профилирования NEVER.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Вызов функции профилирования, уровень профилирования или сочетание вызова и уровня пока не реализованы.|  
|PROFILE_OK|Вызов выполнен успешно.|  
  
## <a name="remarks"></a>Примечания  
 Функции StartProfile и StopProfile управляют состоянием начала и остановки для уровня профилирования. Значение по умолчанию для состояния начала и остановки равно 1. Начальное значение можно изменить в реестре. Каждый вызов StartProfile устанавливает счетчик начала и остановки в значение 1; каждый вызов StopProfile устанавливает его в значение 0.  
  
 Если значение счетчика начала и остановки больше 0, состояние начала и остановки для уровня включено. Если это значение меньше или равно 0, состояние начала и остановки отключено.  
  
 Если состояние начала и остановки, а также состояние приостановки и возобновления включены, состояние профилирования для данного уровня включено. Для профилируемого потока состояния глобального уровня, уровня процесса и потока должны иметь значение ON.  
  
## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Сведения о функции  
 Заголовок: объявлен в файле VSPerf.h  
  
 Библиотека импорта: VSPerf.lib  
  
## <a name="example"></a>Пример  
 Следующий пример показывает использование метода StopProfile. В нем предполагается, что ранее для потока или процесса, определенного идентификатором [PROFILE_CURRENTID](../profiling/profile-currentid.md), был вызван метод StartProfile.  
  
```  
void ExerciseStopProfile()  
{  
    // StartProfile and StopProfile control the   
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)



