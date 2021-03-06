---
title: Строка подключения содержит учетные данные с текстовым паролем и не использует встроенную безопасность | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d1be15ffdc204512c3034662b6ca24955869f5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561710"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Строка подключения содержит учетные данные с текстовым паролем и не использует встроенную систему безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [строка подключения содержит учетные данные с текстовым паролем и не использует встроенную безопасность](https://docs.microsoft.com/visualstudio/data-tools/the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security).  
  
  
Вы хотите сохранить строку подключения к текущему файлу DBML и файлам конфигурации приложения с этой конфиденциальной информацией?  Нажмите кнопку Нет, чтобы сохранить строку подключения без конфиденциальной информации.  
  
 При работе с подключениями к данным, которые содержат конфиденциальную информацию (пароли, которые включены в строку подключения), предоставляется опция сохранения строки подключения в файл DBML проекта и файл конфигурации приложения с или без конфиденциальной информации.  
  
> [!WARNING]
>  Явная установка **подключения** свойства **параметры приложения** свойства **False** добавит пароль в DBML-файл.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения с конфиденциальной информацией в параметрах приложения проекта  
  
-   Нажмите кнопку **Да**.  
  
     Строка подключения сохраняется как параметр приложения. Строка подключения включает конфиденциальную информацию в обычный текст. В файле DBML отсутствует конфиденциальная информация.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения без конфиденциальной информации в параметрах приложения проекта  
  
-   Нажмите кнопку **Нет**.  
  
     Строка подключения сохраняется как параметр приложения, но не включает пароль.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

