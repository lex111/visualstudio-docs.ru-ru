---
title: 'Ошибка: Не установлено средство ASP.NET | Документация Майкрософт'
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
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0617f5200a69809afc86fe9405dc3ea9bd8fcda0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568415"
---
# <a name="error-aspnet-not-installed"></a>Ошибка: не установлено средство ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: приложение ASP.NET не установлено](https://docs.microsoft.com/visualstudio/debugger/error-aspnet-not-installed).  
  
Ошибка возникает при неправильной установке [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] на компьютере, на котором выполняется отладка. Это означает, что либо [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] не было установлено вообще, либо [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] было установлено до установки служб IIS.  
  
### <a name="to-reinstall-aspnet"></a>Переустановка ASP.NET  
  
1.  В окне командной строки введите следующую команду:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     где *версии* представляет номер версии платформы .NET Framework, установленной на компьютере, например v1.0.370. Можно определить версию платформы, просмотрев `\WINDOWS\Microsoft.NET\Framework` каталога.  
  
    > [!NOTE]
    >  В Windows Server 2003 можно установить [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] с помощью **Установка и удаление программ** панели управления.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



