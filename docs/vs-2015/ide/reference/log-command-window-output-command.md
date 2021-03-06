---
title: Команда "Запись вывода окна команд" | Документы Майкрософт
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
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f6cdef31ec8988612815a76c30198e97ddf4c26
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572622"
---
# <a name="log-command-window-output-command"></a>Команда Log Command Window Output
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [журнала команд окна выходных данных команд](https://docs.microsoft.com/visualstudio/ide/reference/log-command-window-output-command).  
  
  
Копирует все входные и выходные данные из окна **Команда** в файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Необязательный. Имя файла журнала. По умолчанию этот файл создается в папке профиля пользователя. Если такое имя файла уже существует, журнал добавляется в конец имеющегося файла. Если файл не указан, используется последний указанный файл. Если предыдущий файл отсутствует, создается файл журнала по умолчанию с именем cmdline.log.  
  
> [!TIP]
>  Чтобы изменить расположение для сохранения файла журнала, введите полный путь. Если этот путь содержит пробелы, заключите его в кавычки.  
  
## <a name="switches"></a>Переключатели  
 /on  
 Необязательный. Запускает ведение журнала для окна **Команда** в указанном файле, добавляя в него новые данные.  
  
 /off  
 Необязательный. Останавливает ведение журнала для окна **Команда**.  
  
 /overwrite  
 Необязательный. Если указанный в аргументе `filename` файл совпадает с существующим файлом, он перезаписывается.  
  
## <a name="remarks"></a>Примечания  
 Если файл не указан, создается файл по умолчанию cmdline.log. По умолчанию эта команда имеет псевдоним Log.  
  
## <a name="examples"></a>Примеры  
 Этот пример создает файл журнала cmdlog и запускает ведение журнала команд.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Этот пример останавливает ведение журнала команд.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 Этот пример возобновляет ведение журнала команд в ранее использовавшемся файле.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



