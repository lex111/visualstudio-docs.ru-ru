---
title: Установка Dotfuscator Community Edition (CE)
ms.date: 06/22/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, защита, бесплатный выпуск, обфускация, .NET, бесплатно, Visual Studio 2017, установка
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Узнайте, как установить бесплатный выпуск Dotfuscator Community Edition, входящий в состав Visual Studio 2017.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: 13027c5d4fe4fc799f6514eb93bfc4ed93141613
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283224"
---
# <a name="install-dotfuscator-community-edition-ce"></a>Установка Dotfuscator Community Edition (CE)

В Visual Studio 2017 представлена новая возможность установки с минимальным влиянием на работу системы.
Dotfuscator Community Edition (Dotfuscator CE) не устанавливается по умолчанию.
Однако процесс установки не вызывает трудностей, даже если вы уже установили Visual Studio.

> [!NOTE]
> Помимо версий Dotfuscator CE, поставляемых с выпусками Visual Studio, PreEmptive Solutions периодически предоставляет обновленные версии на своем веб-сайте.
> Чтобы скачать **последнюю версию** напрямую, а не из установки Visual Studio, **[щелкните здесь, чтобы перейти на страницу скачиваемых файлов Dotfuscator][download]**.

## <a name="within-visual-studio"></a>В среде Visual Studio

Dotfuscator CE можно установить из интегрированной среды разработки Visual Studio.

1. В панели поиска **Быстрый запуск** (CTRL+Q) введите `dotfuscator`. <br/> <br/> ![Быстрый запуск](media/install_from_vs_12.png) <br/> <br/>
2. Результаты появятся на панели быстрого запуска. В разделе *Установка* установите флажок **PreEmptive Protection — Dotfuscator (отдельный компонент)**.
  * Если вы вместо этого в разделе *Меню* видите **Сервис > PreEmptive Protection — Dotfuscator**, то Dotfuscator CE уже установлен. Дополнительные сведения об использовании см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].
3. Откроется окно установщика Visual Studio, автоматически настроенного для установки Dotfuscator CE.
  * Чтобы продолжить, может потребоваться указать учетные данные администратора.
4. Закройте все экземпляры интегрированной среды разработки Visual Studio. <br/> <br/> ![Нажмите кнопку "Установить"](media/install_from_vs_345.png) <br/> <br/>
5. В окне установщика Visual Studio щелкните *Установить*.

После завершения установки можно начать использование Dotfuscator CE. Дополнительные сведения см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].

## <a name="during-visual-studio-installation"></a>Во время установки Visual Studio

Если вы еще не установили Visual Studio 2017, можно получить установщик на [веб-сайте Visual Studio][2017-install].
При запуске он будет отображать варианты установки для выбранного выпуска Visual Studio.

![Параметры установки](media/install_ui.png)

Затем можно установить Dotfuscator CE в качестве отдельного компонента Visual Studio 2017.

1. Откройте вкладку **Отдельные компоненты**.
2. В разделе *Работа с кодом* выберите элемент *PreEmptive Protection — Dotfuscator*.<br/> <br/> ![Отдельные компоненты](media/install_individually_12.png) <br/> <br/>
3. На панели *Сводка* появится *PreEmptive Protection — Dotfuscator* в разделе *Отдельные компоненты*. <br/> <br/> ![Панель итогов](media/install_individually_3.png) <br/> <br/>
4. Настройте другие параметры установки, соответствующие вашей среде.
5. Когда все будет готово для установки Visual Studio, нажмите кнопку *Установить*.

После завершения установки можно начать использование Dotfuscator CE. Дополнительные сведения см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].

## <a name="see-also"></a>См. также

[This topic in the full Dotfuscator CE User Guide]: https://www.preemptive.com/dotfuscator/ce/docs/help/

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]:  https://visualstudio.microsoft.com/downloads/#vs-2017
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html