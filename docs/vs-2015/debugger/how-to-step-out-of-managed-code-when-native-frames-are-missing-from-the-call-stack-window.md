---
title: 'Практическое: шаг с выходом из управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов | Документация Майкрософт'
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
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 682d4f9c8973f8deee65efa0cd8c0d78061ee00a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558942"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Практическое руководство. Выход из пошагового выполнения управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: шаг с выходом из управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов](https://docs.microsoft.com/visualstudio/debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window).  
  
Если код имеет машинные фреймы, которых нет в **стек вызовов** окна, шаг с выходом из управляемого кода может привести к непредвиденным результатам. Чтобы избежать этого, можно использовать точку останова, а не **шаг с выходом**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Выполнение шага с выходом из управляемого кода, когда фрагменты присущего данному объекту кода не отображаются в окне "Стек вызовов"  
  
1.  В присущем данному объекту коде задайте позиционную точку останова после вызова управляемого кода.  
  
2.  На **Отладка** меню, выберите **Продолжить**.  
  
     Когда управляемый вызов завершится, выполнение будет остановлено в точке останова в присущем данному объекту коде.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md)





