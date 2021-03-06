---
title: Переопределение диспетчера содержимого справки
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a02f4af740910fe666af295aa8535c8aef8245c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571742"
---
# <a name="help-content-manager-overrides"></a>Переопределение диспетчера содержимого справки

Вы можете изменить поведение по умолчанию окна справки и связанных со справкой возможностей в интегрированной среде разработки Visual Studio. Некоторые параметры настраиваются путем создания файла [PKGDEF](https://blogs.msdn.microsoft.com/visualstudio/2009/12/18/whats-a-pkgdef-and-why/), с помощью которого задаются различные параметры реестра. Другие указываются непосредственно в реестре.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Управление поведением окна справки с помощью файла PKGDEF

1. Создайте файл *PKGDEF* со следующей первой строкой: `[$RootKey$\Help]`.

2. Добавьте в отдельных строках некоторые или все параметры реестра, описанные в таблице ниже, например `"UseOnlineHelp"=dword:00000001`.

3. Скопируйте файл в папку *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<выпуск\>\Common7\IDE\CommonExtensions*.

4. Выполните команду `devenv /updateconfiguration` в командной строке разработчика.

### <a name="registry-key-values"></a>Параметры реестра

|Значение раздела реестра|Тип|Данные|Описание:|
|------------------|----|----|-----------|
|NewContentAndUpdateService|string|\<URL-адрес http для конечной точки службы\>|Указание уникальной конечной точки службы|
|UseOnlineHelp|dword|`0` для указания справки в Интернете; `1` для указания сетевой справки|Указание справки в Интернете или автономной справки в качестве справки по умолчанию|
|OnlineBaseUrl|string|\<URL-адрес http для конечной точки службы\>|Указание уникальной конечной точки F1|
|OnlineHelpPreferenceDisabled|dword|`0`, чтобы включить параметр справки в Интернете, или `1`, чтобы отключить его|Отключение параметра справки в Интернете|
|DisableManageContent|dword|`0`, чтобы включить вкладку **Управление содержимым** в окне справки, или `1`, чтобы отключить ее|Отключение вкладки **Управление содержимым**|
|DisableFirstRunHelpSelection|dword|`0`, чтобы включить возможности справки, настраиваемые при первом запуске Visual Studio, или `1`, чтобы отключить их|Отключение установки содержимого при первом запуске Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Пример содержимого файла PKGDEF

```
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Использование редактора реестра для изменения поведения окна справки

Путем задания параметров реестра в редакторе реестра можно управлять двумя вариантами поведения.

|Задача|Раздел реестра .|Значение|Данные|
|----------|-----|------|----|
|Переопределение приоритета задания BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (на 64-разрядном компьютере)\Microsoft\Help\v2.3|BITSPriority|**foreground**, **high**, **normal** или **low**|
|Указание на хранилище локального содержимого в сетевой папке с общим доступом|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>См. также

- [Руководство по окну справки для администраторов](../ide/help-viewer-administrator-guide.md)
- [Аргументы командной строки для диспетчера содержимого справки](../ide/command-line-arguments-for-the-help-content-manager.md)
- [Окно справки (Майкрософт)](../ide/microsoft-help-viewer.md)