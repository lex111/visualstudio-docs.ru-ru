---
title: Команда "Заменить в файлах" | Документы Майкрософт
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
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8df474b7ca65983d7bf7203e2d3e2146fbede6f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573263"
---
# <a name="replace-in-files-command"></a>Команда Replace In Files
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [заменить в файлах-команда](https://docs.microsoft.com/visualstudio/ide/reference/replace-in-files-command).  
  
  
Заменяет текст в файлах с использованием подмножества параметров, доступных на вкладке **Заменить в файлах** окна **Поиск и замена**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## <a name="arguments"></a>Аргументы  
 `findwhat`  
 Обязательно. Текст для поиска совпадения.  
  
 `replacewith`  
 Обязательно. Текст для замены совпавшего текста.  
  
## <a name="switches"></a>Переключатели  
 /all или /a  
 Необязательный. Заменяет все вхождения искомого текста на замещающий текст.  
  
 /case или /c  
 Необязательный. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.  
  
 /ext: `extensions`  
 Необязательный. Определяет расширения файлов, в которых будет проводиться поиск.  
  
 /keep или /k  
 Необязательный. Указывает, что все измененные файлы остаются открытыми.  
  
 /lookin: `searchpath`  
 Необязательный. Каталог, в котором будет производиться поиск. Если путь содержит пробелы, необходимо заключить полный путь в кавычки.  
  
 /options или /t  
 Необязательный. Отображает список текущих параметров поиска, но не выполняет сам поиск.  
  
 /regex или /r  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset или /e  
 Необязательный. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.  
  
 /stop  
 Необязательный. Останавливает выполнение текущей активной операции поиска. Если указан аргумент `/stop`, остальные аргументы при замене игнорируются. Например, чтобы остановить текущую замену, нужно ввести следующую строку:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 /sub или /s  
 Необязательный. Выполняет поиск в папках, вложенных в каталог, который указан в аргументе /lookin:`searchpath`.  
  
 /text2 или /2  
 Необязательный. Отображает результаты замены в окне **Результаты поиска 2**.  
  
 /wild или /l  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.  
  
 /word или /w  
 Необязательный. Выполняет поиск только целых слов.  
  
## <a name="example"></a>Пример  
 Этот пример ищет `btnCancel` и заменяет на `btnReset` во всех CLS-файлах, расположенных в папке "my visual studio projects", а также отображает сведения о заменах в окне **Результаты поиска 2**.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## <a name="see-also"></a>См. также  
 [Поиск и замена текста](../../ide/finding-and-replacing-text.md)   
 [Заменить в файлах](../../ide/replace-in-files.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



