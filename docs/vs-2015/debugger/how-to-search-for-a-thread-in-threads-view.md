---
title: 'Практическое: поиск потока в представлении "Потоки" | Документация Майкрософт'
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
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 071b32a6f8947289d12ad8a402a316b1d174f65f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571884"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Практическое руководство. Поиск потока в представлении потоков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: поиск потока в представлении потоков](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-thread-in-threads-view).  
  
Конкретным потоком в представление "Потоки" можно найти с помощью его поток идентификатор или строку модуля в качестве критерия поиска. Можно также указать исходное направление поиска. Поля в диалоговом окне отобразятся атрибуты потока, выбранного в дереве потоков.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Поиск потока в представлении потоков  
  
1.  Расположите окна таким образом, Spy ++ и активная [представление "Потоки"](../debugger/threads-view.md) окна являются видимыми.  
  
2.  Из **поиска** меню, выберите **найти поток**.  
  
     [Потоков диалоговое окно поиска](../debugger/thread-search-dialog-box.md) открывает.  
  
3.  Введите идентификатор потока или строку модуля в качестве условия поиска.  
  
4.  Очистите все поля, для которых вы не хотите указать значения.  
  
    > [!TIP]
    >  Чтобы найти все потоки, принадлежащие модулю, снимите **потоков** текстовое поле и введите модуль имя в **модуль** поле. Затем с помощью **Найти далее** для продолжения поиска потоков.  
  
5.  Выберите **вверх** или **вниз** для исходное направление поиска.  
  
6.  Нажмите кнопку **ОК**.  
  
 Если найден соответствующий поток, то он выделяется в окне представления потоков.



