---
title: Включение параметров отладки в Visual C++ (-D_DEBUG) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5298879d93bf4e86df7610d5891e73bdbb67c4a1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472582"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Включение параметров отладки в Visual C++ (/D_DEBUG)
В [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], возможности отладки, такие как утверждения, доступны при компиляции программы с заданным символом **_DEBUG** определен. Можно определить **_DEBUG** одним из двух способов:  
  
-   Укажите **#define _DEBUG** в исходном коде, или  
  
-   Укажите **/D_DEBUG** параметр компилятора. (При создании проекта в Visual Studio с использованием мастеров, **/D_DEBUG** определяется автоматически в конфигурации отладчика.)  
  
 Когда **_DEBUG** будет определена, компилятор компилирует разделы кода, окруженный **#ifdef _DEBUG** и `#endif`.  
  
 Конфигурация отладчика программы MFC должна компоноваться с версией отладчика библиотеки MFC. Файлы заголовков MFC определяют правильную версию для компоновки библиотеки MFC на основе символов, которые вы определили, таких как **_DEBUG** и **_UNICODE**. Дополнительные сведения см. в разделе [версии библиотек MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)