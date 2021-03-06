---
title: Практическое руководство. Указание двоичного файла для запуска | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec65dd3a5bcc812ff2f7c42ae4cbbba6080664db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563788"
---
# <a name="how-to-specify-the-binary-to-start"></a>Практическое руководство. Указание двоичного файла для запуска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: указание двоичного файла для начала](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-binary-to-start).  
  
Для профилирования двоичных файлов, таких как библиотеки DLL, необходимо ввести сведения в диалоговом окне **Страницы свойств \<целевой объект>**. Эти сведения указывают расположение проекта DLL для вызывающего приложения.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Указание исполняемого файла для запуска  
  
1.  В **обозревателе производительности** щелкните правой кнопкой мыши целевой двоичный файл и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Страницы свойств** щелкните **Запуск**.  
  
3.  Установите флажок **Переопределить свойства проекта**.  
  
4.  В текстовом поле **Исполняемый файл для запуска** укажите расположение файла.  
  
5.  В текстовом поле **Аргументы** укажите аргументы, необходимые для запуска приложения.  
  
6.  В текстовом поле **Рабочий каталог** укажите расположение каталога.  
  
7.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)



