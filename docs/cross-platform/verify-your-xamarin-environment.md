---
title: Проверка окружения Xamarin | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: e46da7cf39ad816f70454983c56dd5751981f741
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495767"
---
# <a name="verify-your-xamarin-environment"></a>Проверка окружения Xamarin

После завершения работы установщиков (см. [Setup and install](../cross-platform/setup-and-install.md)) потратьте несколько минут на проверку готовности системы к разработке приложений в Xamarin.

 После завершения проверки установки попробуйте выполнить одно или оба указанных ниже пошаговых руководства:

-   [Основы создания приложений с помощью Xamarin.Forms в Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md), чтобы научиться создавать приложения с помощью Xamarin.Forms.

-   [Создание приложений с нативным пользовательским интерфейсом с использованием Xamarin в Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md), чтобы научиться использовать нативные пользовательские интерфейсы на каждой платформе, но при этом совместно использовать часть кода в библиотеке .NET Standard.

## <a name="all-platforms"></a>Все платформы

В Visual Studio выберите **Сервис** > **Расширения и обновления** и проверьте, не требуется ли обновление каких-либо компонентов Xamarin.

Затем создайте новое решение Xamarin.Forms в Visual Studio, выбрав **Файл** > **Новый проект**. В диалоговом окне разверните **Visual C#** > **Кроссплатформенный**, выберите **Мобильное приложение (Xamarin.Forms)** и нажмите кнопку **ОК**. В следующем диалоговом окне выберите **Пустое приложение**. В разделе **Стратегия совместного использования кода** выберите **.NET Standard**. Нажмите кнопку **ОК**.

В результате этих действий будет создано решение с четырьмя проектами: проект с общей библиотекой .NET Standard 2.0 и проекты приложений для Android, iOS и универсальной платформы Windows (UWP):

![Результат создания нового проекта из шаблона пустого приложения Xamarin.Forms](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")

## <a name="android"></a>Android

1. Убедитесь, что установлена последняя версия Android SDK Tools, для этого откройте **Сервис > Android > Диспетчер пакетов SDK Android**. Установите последние версии Android SDK Tools, Android SDK Platform Tools и Android SDK Build tools. Устанавливать самый последний уровень API Android нет необходимости. Необходимый уровень API зависит от уровня платформы, для которой вы будете разрабатывать приложения. Обычно при установке платформы Xamarin устанавливается требуемый уровень платформы Android.

2.  Проверка сборки и отладки на устройстве или в эмуляторе:

    -   В обозревателе решений щелкните правой кнопкой мыши проект Android и выберите команду **Назначить запускаемым проектом**.

    -   На панели инструментов появится раскрывающийся список, содержащий доступные устройства и эмуляторы Android.

    На устройствах Android должна быть включена отладка по USB в параметрах разработчика на странице настроек. Затем необходимо подключить устройство к компьютеру с помощью кабеля USB.

    Также отображается список эмуляторов. Выберите устройство или эмулятор Visual Studio:

  ![Выбор эмулятора Visual Studio для Android в качестве целевого объекта отладки](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")

  Дополнительные сведения см. в статье [Введение в эмулятор Visual Studio для Android](https://blogs.msdn.microsoft.com/devops/2014/11/12/introducing-visual-studios-emulator-for-android/) в блоге Microsoft DevOps. При возникновении проблем с запуском эмулятора см. статью об [устранении неполадок эмулятора Android для Visual Studio](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Можно также создать новые профили устройств для эмулятора, выбрав **Сервис > Android > Диспетчер эмуляторов Android**.

3. Нажмите клавишу **F5**, чтобы скомпилировать и развернуть программу на устройстве или эмуляторе Android.

## <a name="windows"></a>Windows

1.  В обозревателе решений щелкните правой кнопкой мыши проект приложения для универсальной платформы Windows и выберите команду **Назначить запускаемым проектом**.

2.  В раскрывающемся списке **Платформы решения** выберите **x86** или **x64**. Выберите **Локальный компьютер**.

3.  Нажмите клавишу **F5**, чтобы развернуть программу на рабочем столе.

## <a name="ios"></a>iOS

1.  Убедитесь, что компьютер Mac доступен в сети и связан с Visual Studio, как описано в статье [Подключение к Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/).

2.  В обозревателе решений щелкните правой кнопкой мыши проект iOS и выберите команду **Назначить запускаемым проектом**.

3.  Выберите в качестве целевого объекта **iPhoneSimulator** из раскрывающегося списка сборки Visual Studio, как показано ниже, или **iPhone**, если имеется связанное с компьютером Mac устройство.

 ![Выбор целевого объекта сборки iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "Проверка CrossPlat Xamarin 5")

 Если в списке нет симуляторов, запустите Xcode на компьютере Mac, выберите **Xcode** > **Preferences** (Xcode > Параметры) и нажмите кнопку **Download** (Скачать). В разделе **Components** (Компоненты) вы должны увидеть доступные для скачивания версии симулятора. Дополнительные инструкции по отладке можно найти на странице Xamarin [Отладка iOS](/xamarin/ios/deploy-test/debugging-in-xamarin-ios).

4.  Выберите целевой эмулятор устройства из раскрывающегося списка в Visual Studio:

 ![Выбор целевого объекта отладки iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "Проверка CrossPlat Xamarin 6")

5. Запустите отладчик, нажав клавишу **F5**. На компьютере Mac откроется симулятор, где можно будет взаимодействовать с приложением во время отладки из Visual Studio. Если у вас есть физический iPhone или iPad, подключенный к Mac, они отобразятся в списке, чтобы вы могли выбрать их. Если не отображается ни одного устройства или симулятора, проверьте подключение к компьютеру Mac. Ознакомьтесь со статьей, на которую дана ссылка на шаге 1 выше, или последовательно выберите **Сервис** > **iOS** > **Связать с Mac**.

6.  Если возникли проблемы с подключением к Mac, ознакомьтесь со статьей [Устранение неполадок подключения для узла сборки Xamarin.iOS](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/).

7.  Если отображается ошибка "Нет установленных профилей подготовки, которые соответствуют установленным ключам подписи iOS", попробуйте выполните следующие рекомендации:

  - Убедитесь, что учетная запись Apple ID добавлена в Xcode на компьютере Mac, как описано в статье о [добавлении учетной записи в Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) на сайте apple.com.  После добавления учетной записи перезапустите Visual Studio и Xcode.

  - Убедитесь, что в свойствах проекта iOS на вкладке подписывания пакета iOS поле Custom (Настраиваемые) пусто для активной конфигурации отладки.  Примечание. Удалять этот параметр следует, только если отображается указанное выше сообщение об ошибке.

  ![Проверка CrossPlat Xamarin 8](../cross-platform/media/crossplat-xamarin-verify-8.png "Проверка CrossPlat Xamarin 8")
