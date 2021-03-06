---
title: Приступая к работе с диагностикой графики Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 05/26/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 069dd7638296987c195fbae6cc9d858fdd3421ee
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058676"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Начало работы с диагностикой графики Visual Studio
В этом разделе вы подготовитесь к первому использованию диагностики графики, а затем запишите кадры из приложения Direct3D и проверите их в анализаторе графики.  
  
## <a name="requirements"></a>Требования  
 Чтобы использовать диагностику графики в Visual Studio, необходимо использовать Visual Studio Enterprise, Visual Studio Professional или Visual Studio Community.  Эта функция не содержат другие выпуски, включая Visual Studio Code.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Необходимые компоненты для Windows 10  
 Дополнительный компонент Windows *графические инструменты* предоставляет инфраструктуру записи и воспроизведения, которые требуются для диагностики графики в Windows 10.  
  
 Сведения об установке графических инструментов см. в разделе [Установка графических инструментов для Windows 10](#InstallGraphicsTools).  
  
##  <a name="InstallGraphicsTools"></a> Установка графических инструментов для Windows 10  
 В Windows 10 инфраструктура диагностики графики предоставляется дополнительным компонентом Windows вызывается *графические инструменты*. Данный компонент необходим для записи и воспроизведения графической информации в Windows 10 независимо от того, производится ли запись для приложения, настроенного на предыдущую версию Windows, и какую версию Direct3D оно использует. Вы можете установить компонент графических инструментов заранее; в противном случае он будет установлен по требованию при первом запуске сеанса диагностики графики из Visual Studio.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Установка графических инструментов для Windows 10  
  
1.  В поле поиска введите **программы и компоненты** и откройте **приложения и возможности** параметры.
  
3.  В правой части **приложения и возможности** диалоговом окне выберите **управление дополнительными компонентами** (в разделе **приложения и возможности**).

    **Управление дополнительными компонентами** откроется диалоговое окно.
  
4.  В **управление дополнительными компонентами** диалоговом окне выберите **добавить компонент**. Появится список дополнительных компонентов, которые можно установить.  
  
5.  Выберите **графические инструменты** в списке функций выберите **установить**.  
  
 Компонент графических инструментов также устанавливается автоматически при установке пакета SDK для Windows 10.  
  
> [!TIP]
>  Дополнительный компонент графических инструментов Windows 10 предоставляет упрощенные возможности записи и воспроизведения, например программу командной строки для захвата **dxcap.exe**, который может использоваться в поддержки, тестирования и диагностики на компьютеры, где не установлены инструменты разработчика. Дополнительные сведения см. в разделе [программа командной строки для захвата](command-line-capture-tool.md) раздела.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Использование диагностики графики в первый раз  
 Теперь, когда у вас есть все необходимое, можно приступать к использованию диагностики графики. Выполните следующие действия.  
  
### <a name="1---create-a-direct3d-app"></a>1 Создание приложения Direct3D  
 Если у вас уже есть собственное приложение Direct3D для изучения диагностики графики, отлично! В противном случае используйте одно из следующих:

- **Приложение DirectX 11 (универсальные Windows)** или **приложение DirectX 12 (универсальной Windows)** шаблоны проектов для Windows 10.
- [Образцом Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) для Windows 10.  
  
 Прежде чем продолжить убедитесь, что можете выполнить сборку приложения.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 Запуск сеанса диагностики графики  
 Теперь все готово для запуска первого сеанса диагностики графики. В Visual Studio в главном меню выберите **отладка, графика, начать отладку графики**, или просто нажмите **Alt + F5**. При этом ваше приложение запускается в режиме диагностики графики и отображаются окна сеанса диагностики в Visual Studio.  
  
> [!IMPORTANT]
>  Если приложение запускается в Windows 10 и еще не был установлен дополнительный компонент графических инструментов, вам будет предложено сделать это. Необходимо установить этот компонент, прежде чем можно будет использовать диагностику графики в Windows 10.  
  
### <a name="3---capture-frames"></a>3 Запись кадров  
 Вы можете записывать кадры сразу после запуска приложения.  
  
#### <a name="to-capture-single-frames"></a>Запись отдельных кадров  
  
-   В Visual Studio, выберите **захватить кадр** кнопки в окне сеанса для графических инструментов или диагностики. Или, если ваше приложение имеет фокус, просто нажмите клавиши **Print Screen** на клавиатуре.
  
#### <a name="to-capture-a-sequence-of-frames"></a>Запись последовательности кадров  
  
-   В Visual Studio в окне сеанса диагностики установите **кадров для захвата** число кадров для записи в последовательности, затем запишите последовательность с помощью любого из методов, описанных выше для отдельных кадров.  
  
     Для отдельных кадров снова, задайте **кадров для захвата** для *1*.  
  
 После завершения записи кадров просто выйдите из приложения или выберите **остановить** кнопку из панели инструментов графики или в окне сеанса диагностики.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 — Проверка записанных кадров в анализаторе графики  
 Теперь все готово для анализа полученных кадров. Чтобы начать анализ кадра, выберите номер соответствующего кадра в окне сеанса диагностики. Это кадр открывается в **анализатора графики**, где вы можете использовать средства диагностики графики для анализа, как ваше приложение использует Direct3D для отслеживания проблем отрисовки, или использовать **анализ кадров** инструмент, сведения о его производительности.  
  
 Если вы выбрали неверный кадр в окне сеанса диагностики или вы хотите проанализировать другой кадр, можно выбрать новый кадр в анализаторе графики. На **целевой объект отрисовки** вкладку окна журнала графики в области образа цели отрисовки разверните **список кадров** и выберите другой кадр для изучения.  
  
 Дополнительные сведения о том, как совместное использование инструментов анализа графики, см. в разделе [примеры](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>См. также  
 [Direct3D 12 графики](/windows/desktop/direct3d12/direct3d-12-graphics)