---
title: Диалоговое окно "Дополнительные параметры безопасности" | Документы Майкрософт
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
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72b8bb7f6301672e89c54c9fa73a72bad8148999
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560609"
---
# <a name="advanced-security-settings-dialog-box"></a>Диалоговое окно "Дополнительные параметры безопасности"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Advanced Security диалоговое окно параметров](https://docs.microsoft.com/visualstudio/ide/reference/advanced-security-settings-dialog-box).  
  
  
В этом диалоговом окне можно задать параметры безопасности, связанные с отладкой в зоне.  
  
 Чтобы открыть это диалоговое окно, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. Когда откроется окно **Конструктор проектов**, перейдите на вкладку **Безопасность**. На странице **Безопасность** установите флажок **Включить параметры безопасности ClickOnce-приложений**, установите переключатель **Это приложение с частичным доверием** и нажмите кнопку **Дополнительно**.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Отладить это приложение с выбранным набором разрешений**  
 Если этот флажок установлен, набор разрешений, выбранный на странице **Безопасность**, будет использоваться во время отладки. Этот параметр выбран по умолчанию.  
  
 Для выполнения отладки в зоне безопасности этот параметр должен быть включен, кроме того, нужно активировать параметр **Включить ведущий процесс Visual Studio** (на странице **Отладка** **конструктора проектов**).  
  
 Для проектов приложений браузера WPF флажок **Отладить это приложение с выбранным набором разрешений** установлен и отключен.  
  
 **Предоставить приложению доступ к своему исходному веб-сайту**  
 Если этот флажок установлен, приложение сможет получить доступ к веб-сайту или общему ресурсу сервера, где оно опубликовано. Этот параметр выбран по умолчанию.  
  
 **Отладить это приложение как загруженное со следующего URL**  
 Если приложению нужно разрешить доступ к веб-сайту или общему ресурсу сервера, соответствующим значению **URL-адрес установки**, указанному на странице **Публикация**, введите здесь этот URL-адрес. Этот параметр доступен, только если установлен флажок **Предоставить приложению доступ к своему исходному веб-сайту**.  
  
## <a name="see-also"></a>См. также  
 [Страница "Безопасность" в конструкторе проектов](../../ide/reference/security-page-project-designer.md)



