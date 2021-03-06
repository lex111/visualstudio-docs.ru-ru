---
title: 'Практическое: изменение машины воспроизведения диагностики графики | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33d2acc46cbf92c9b2bbd699903ad3169661a54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562582"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Практическое руководство. Изменение машины воспроизведения диагностики графики
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: изменение машины воспроизведения диагностики графики](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-change-the-graphics-diagnostics-playback-machine).  
  
Вы можете воспроизведения графической информации с помощью локального компьютера или с помощью удаленного компьютера или устройства.  
  
## <a name="choosing-a-playback-machine"></a>Выбор компьютера воспроизведения  
 Компьютер воспроизведения — это компьютер или устройство, который используется для воспроизведения событий графики из журнала графики. Как правило локальный компьютер — самый удобный вариант, но проблема отрисовки может не воспроизвестись на компьютере, с оборудованием или версиями драйверов компьютера, где она была записана; в этом случае можно выбрать удаленный компьютер воспроизведения, лучше воспроизводит проблему и по-прежнему использовать свой компьютер разработки для ее диагностики.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Использование локального компьютера для воспроизведения графической информации  
  
1.  В окне документа журнала графики выберите **компьютер воспроизведения** ссылку. **Подключения к удаленному отладчику** откроется диалоговое окно.  
  
2.  В разделе **Настройка вручную**в **адрес** свойство, введите `localhost`.  
  
3.  Задайте **режим проверки подлинности** свойства **None**.  
  
4.  Выберите **выберите** кнопки.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Использование удаленного компьютера для воспроизведения графической информации  
  
1.  В окне документа журнала графики выберите **компьютер воспроизведения** ссылку. **Подключения к удаленному отладчику** откроется диалоговое окно.  
  
2.  В разделе **Настройка вручную**в **адрес** свойство, введите имя домена Windows или IP-адрес компьютера или устройства, которое вы хотите использовать для воспроизведения графической информации.  
  
3.  Укажите тип авторизации, который вы хотите использовать для защиты подключения к компьютеру воспроизведения.  
  
    -   Для аутентификации Windows задайте **режим проверки подлинности** свойства **Windows**.  
  
    -   Без проверки подлинности, задайте **режим проверки подлинности** свойства **None**.  
  
4.  Выберите **выберите** кнопки.  
  
> [!NOTE]
>  **Подключения к удаленному отладчику** диалоговое окно может также отображаться удаленные целевые объекты отладки, которые напрямую подключены к компьютеру разработки или находятся в той же подсети. Один из этих удаленных целевых объектов отладки можно использовать как компьютер воспроизведения диагностики графики без настройки вручную. В **подключения к удаленному отладчику** диалоговом окне выберите целевой объект и затем задайте **выберите** кнопку.  
  
## <a name="see-also"></a>См. также  
 [Документ журнала графики](../debugger/graphics-log-document.md)



