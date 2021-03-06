---
title: Команда "Перейти" | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 123398be5bf8b4aece11e2624390507cec2252d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561568"
---
# <a name="go-to-command"></a>Команда Go To
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [для команды Go](https://docs.microsoft.com/visualstudio/ide/reference/go-to-command).  
  
  
Перемещение курсор на указанную строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Аргументы  
 `linenumber`  
 Необязательный. Целое число, задающее номер строки, к которой нужно перейти.  
  
## <a name="remarks"></a>Примечания  
 Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.  
  
 Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.  
  
 Эта команда имеет псевдоним GoToLn.  
  
## <a name="example"></a>Пример  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



