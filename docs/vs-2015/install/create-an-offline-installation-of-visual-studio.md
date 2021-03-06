---
title: Создание автономной установки Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 31273fc8abb59661351cc50bcaca7da5a5b8612e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562969"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Создание автономной установки Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последние версии документации Visual Studio 2017, см. в разделе [установка Visual Studio 2017 на низкой пропускной способностью или ненадежных сетевых средах](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network), или [Создание сетевой установки Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio) и [Особые рекомендации по установке Visual Studio 2017 в автономной среде](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment).

Этой странице описывается установка Visual Studio 2015, когда вы не подключены к Интернету. Тем не менее для выполнения установки «разъединенное», необходимо сначала создать макета автономной установки с компьютера, подключенного к Интернету. Вот как это делается.  
  
> [!IMPORTANT]
>  Если автономный компьютер работает под управлением Windows 7 с пакетом обновления 1 или Windows Server 2008 R2, см. специальные инструкции в [Устранение неполадок автономной установки](#BKMK_tshoot) этого раздела.  Выполните эти инструкции *перед* установке Visual Studio 2015.  
  
##  <a name="BKMK_Offline"></a> Установка путем создания автономной установки  
  
#### <a name="to-create-an-offline-installation-layout"></a>Чтобы создать структуру установки в автономном режиме  
  
1.  Выберите выпуск Visual Studio, вы хотите установить из [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) странице загрузки.  
  
2.  После загрузки установщика в расположение в файловой системе, запустите "\<имя исполняемого файла >/Layout».  
  
     Например выполните: `vs_enterprise.exe /layout D:\VisualStudio2015`  
  
     С помощью `/layout` switch, можно скачать почти все пакеты установки, не только те, которые применяются к компьютеру загрузки. Такой подход позволяет файлы, которые необходимо запустить этот установщик в любом месте и может оказаться полезным, если вы хотите установить компоненты, которые не были установлены изначально.  
  
3.  После выполнения этой команды, диалоговое окно появится, позволяющий изменить папку макета автономной установки, будет размещена.   Затем щелкните **загрузить** кнопки.  
  
     После успешной загрузки пакета вы увидите сообщение о **Установка успешно завершена! Все указанные компоненты успешно получены.**  
  
4.  Найдите папку, созданную ранее. (Например, найдите D:\VisualStudio2015.) Эта папка содержит все необходимое для копирования в общую папку или на установочный носитель.  
  
    > [!CAUTION]
    >  В настоящее время пакет SDK для Android не поддерживает автономную установку. Если попытаться установить компоненты пакета SDK для Android на компьютере, который не подключен к Интернету, может произойти сбой установки. Дополнительные сведения см. в разделе «Устранение неполадок автономной установки» в этом разделе.  
  
5.  Запустите установку из расположения файла или с установочного носителя.  
  
## <a name="updating-an-offline-installation"></a>Обновление автономной установки  
 Корпорация Microsoft выпустила несколько обновлений для Visual Studio 2015. Чтобы обновить установку Visual Studio, просто загрузите выпуск из из [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) странице загрузки. Затем выполните действия, описанные в этом разделе, чтобы создать макет автономной установки и затем использовать его для обновить установленную копию Visual Studio 2015.  
  
##  <a name="BKMK_tshoot"></a> Устранение неполадок автономной установки  
 При автономной установке из кэша установки могут выводиться предупреждения о невозможности установить некоторые компоненты и пакеты. В таблице ниже приведены возможные решения таких проблем.  
  
|Компонент или пакет|Решение|  
|--------------------------|--------------|  
|Dotfuscator и Analytics Community Edition 5.19.1 (для выпусков Community, Professional и Enterprise, Visual Studio, так как установлена на **Windows 7 с пакетом обновления 1** и **Windows Server 2008 R2**)|Если автономный компьютер работает под управлением **Windows 7 с пакетом обновления 1** или **Windows Server 2008 R2**, перед установкой Visual Studio 2015, необходимо выполнить следующие действия:<br /><br /> 1.  Настройте файловый или веб-сервер для загрузки файлов списка доверия Сертификатов.<br /><br /> 2.    Redirect the Microsoft Automatic Update URL для отключенных сред.<br /><br /> Дополнительные сведения см. в разделе [Настройка доверенных корневых сертификатов и запрещенных сертификатов](https://technet.microsoft.com/library/dn265983.aspx) страницу на сайте Microsoft TechNet.|  
|Программа установки Android SDK (уровень API)|Для установки пакетов Android SDK (уровень API) требуется подключение к Интернету. Если вы находитесь в сети с ограниченным доступом, при установке Visual Studio необходимо разрешить доступ к следующим URL-адресам:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Дополнительные сведения об устранении возможных проблем с параметрами прокси-сервера см. в разделе [сбоев (программа установки Android SDK) используется прокси-установки Visual Studio 2015](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) записи блога.|  
|Шаблоны элементов расширения среды Visual Studio<br /><br /> Расширение GitHub для Visual Studio<br /><br /> Инструменты PowerShell для Visual Studio|Если у вас нет подключения к Интернету при установке Visual Studio 2015, можно использовать специальный автономный канал для создания макета автономной установки. **Примечание:** этот специальный веб-канал содержит самые последние обновления для Visual Studio 2015. <br /><br /> Чтобы создать специальную автономный канал, выполните следующую команду: / Layout *диска:* \VisualStudio2015 /overridefeeduri *URL-адрес для веб-канала xml*<br /><br /> Например для английского языка специальные автономный канал Visual Studio 2015 Enterprise, выполните следующую команду:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Полный список URL-адреса, которые можно использовать для создания специальной автономный канал на языке по своему усмотрению см. в следующей таблице.|  
  
 Используйте следующие URL-адреса для создания специальных автономного канала конкретного языка, как описано в приведенной выше таблице.  
  
|Язык|URL-адрес|  
|--------------|---------|  
|Китайский (упрощенное письмо)|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804|  
|Китайский (традиционное письмо)|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404|  
|Чешский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405|  
|Немецкий|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407|  
|Английский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409|  
|Испанский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A|  
|Французский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C|  
|Итальянский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410|  
|Японский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411|  
|Корейский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412|  
|Польский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415|  
|португальский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416|  
|Русский|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419|  
|Турецкий|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F|  
  
## <a name="see-also"></a>См. также  
 [Установка Visual Studio]()